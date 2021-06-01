Title: Release Process

We'll be using the [Apache Nexus repository](http://repository.apache.org) for
releasing SNAPSHOT and release artifacts.  More details on releasing
artifacts and using Nexus can be found on the Maven website at
[http://maven.apache.org/developers/release/apache-release.html](http://maven.apache.org/developers/release/apache-release.html).

<a name="ReleaseProcess-ReleaseSteps"></a>
### Release Steps

1. Environment setup for releasing artifacts (same for `SNAPSHOT`s and
releases)
    1. Use the latest Oracle 8 JDK (with javafx, it's required by the TCK!)
    1. Use Maven 3.2.1 or later
    1. Make sure the [Release Setup][] steps have been performed.

1. Prepare the source for release: 
    1. Clean up JIRA so the **Fix Version** in issues resolved since the last
       release includes this release version correctly.  Also, transition any
       **Resolved** issues to the **Closed** state.
    1. Update the text files in a working copy of the project root:
        1. Update the `CHANGES.txt` based on the Text release reports from JIRA.
        1. Review and update `README.txt` if needed.
        1. Commit any changes back to GIT:

```sh
                git commit -a -m "updating files for release" & git push
```

    1. Stage any Roadmap or Release landing pages on the wiki.
    1. Use `mvn apache-rat:check` to verify the source has the required headers before
       trying to release.
    1. Perform a full build and deploy the SNAPSHOT artifacts:

```sh
            mvn -Papache-release clean deploy
```

    1. Inspect the files in your local target directories to ensure:
        1. All jars and zips include `LICENSE` and `NOTICE` files
        1. The NOTICE files cover all third-party included files (like XSD
schemas)
        1. The `LICENSE` files include any third-party licenses (none at this time)
        1. All jars/zips/poms have `.asc` (PGP signature) files

1. Do a dry run of the release:prepare step.
 The dry run will not commit any changes back to GIT and gives you the
opportunity to verify that the release process will complete as expected.
You will be prompted for the following information :
    1. Release version - take the default - (default 1.0)
    1. SCM release tag - take the default - (default 1.0)
    1. New development version - take the default - (default 1.0.1-SNAPSHOT)
    1. *optional* if you have not specified a GPG passphrase in settings.xml
you will be prompted for it:

```sh
            mvn -Papache-release release:prepare -DdryRun=true
```

        Sample output:

```text
            [INFO] Working directory: /Users/drwoods/bval/1.0-rc1
            [INFO] Checking dependencies and plugins for snapshots ...
            What is the release version for "Apache BVal :: bval-parent (Parent POM)"? (org.apache.bval:bval-parent) 1.0: : 
            What is SCM release tag or label for "Apache BVal :: bval-parent (Parent POM)"? (org.apache.bval:bval-parent) bval-parent-1.0: : 1.0
            What is the new development version for "Apache BVal :: bval-parent (Parent POM)"? (org.apache.bval:bval-parent) 1.0.1-SNAPSHOT: : 
            [INFO] Transforming 'Apache BVal :: bval-parent (Parent POM)'...
```

         *If you cancel a release:prepare before it updates the pom.xml versions,
         then use the `release:clean` goal to just remove the extra files that were
         created.*

1. Verify that the release process completed as expected:
    1. The release plugin will create `pom.xml.tag` files which contain the
     changes that would have been committed to GIT. The only differences between
     `pom.xml.tag` and its corresponding `pom.xml` file should be the version
     number.
    1. If other formatting changes have been made you should review the changes
and then commit them:

```sh
            git commit -a -m "fixing formatting for release" & git push
```

    1. Assuming the `.tag` files look OK you may proceed and do any other
validation you feel necessary. The following list may be helpful:
        1. Check release.properties and make sure that the scm properties have the
right version. Sometimes the scm location can be the previous version not
the next version.
        1. [Verify signatures](#ReleaseProcess-Verifyingreleasesignatures)
    1. Once any failures or required updates have been committed to GIT,
rollback the release prepare files:

```sh
            mvn -Papache-release release:rollback
```

1. Prepare the release

    Run the `release:prepare` step for real this time.  You'll be prompted
for the same version information and optionally your GPG passphrase again.

     **Different arguments and steps are required as there are problems with
the maven-jar-plugin and maven-release-plugin when using the test-jar goal.
See [http://jira.codehaus.org/browse/MJAR-68](http://jira.codehaus.org/browse/MJAR-68)
and [http://jira.codehaus.org/browse/MRELEASE-285](http://jira.codehaus.org/browse/MRELEASE-285).**

```sh
        mvn -Papache-release release:prepare
```

1. Backup (zip or tar) your local release candidate directory in case you
need to rollback the release after the next step is performed.

```sh
        cd ..
        tar -czf 1.0-rc1.tar.gz 1.0-rc1/
        cd 1.0-rc1
```

1. Perform the release:
    1. This step will create a maven staging repository and site for use in
     testing and voting. You will be prompted for your **repository.apache.org**
     and **people.apache.org** password several times if you have not added
     server profiles to your `settings.xml`.
     See [Release Setup](/release-setup.html) for more information. 

```sh
            mvn -Papache-release release:perform [-Duser.name=<your_apache_uid>]
```

1. Verify the release artifacts:
    1. Verify the staged artifacts in the nexus repo:
        1. [https://repository.apache.org/index.html](https://repository.apache.org/index.html)
        1. **Build Promotion --> Staging Repositories**
        1. Navigate through the artifact tree and make sure that all binary, `javadoc`,
         `sources`, and `tests` jars, as well as `pom`s, ... have `.asc` (GPG signature) and `.md5`
         files (see [Repository FAQ][] and [Detached Signatures][]). The `source-release.zip` of `bval-parent`
         should likewise have signature and checksum files.
    1. Upload the source artifacts to the dev dist area via SVN at
         `https://dist.apache.org/repos/dist/dev/bval/<version>/source`
         (./target/bval-parent-<version>-source-release.zip and the .asc + .sha512 file)
    1. Check out the newly created tag and build the site using `mvn post-site`.
    1. Verify the HTML links in `target/staging/index.html` are correct
    1. Commit the contents of `target/staging` to `https://dist.apache.org/repos/dist/dev/bval/<version>/site/`
    1. Close the nexus staging repo:
        1. [https://repository.apache.org/index.html](https://repository.apache.org/index.html)
        1. **Build Promotion --> Staging Repositories**
        1. Click the checkbox to select the open `org.apache.bval-XXX` staging repo,
         then click the **Close** button on the toolbar above.

1. Put the release candidate up for a vote:
    1. Create a `VOTE` email thread on [bval-dev](mailto:dev@bval.apache.org) to record votes as replies, e.g.:

```text
            To: dev@bval.apache.org
            Subject: [VOTE] Apache BVal <version> Release Candidate

            I've created a <version> release candidate, with the following artifacts up for a vote:

            Git source tag:
            https://gitbox.apache.org/repos/asf?p=bval.git;a=tags

            Maven staging repo:
            https://repository.apache.org/content/repositories/orgapachebval-020/

            Source release:
            https://dist.apache.org/repos/dist/dev/bval/2.0.0-RC1 (r9999)

            Generated site:
            https://dist.apache.org/repos/dist/dev/bval/2.0.0-RC1/site/index.html

            PGP release keys:
            http://www.apache.org/dist/bval/KEYS

            The vote will be open for at least 72 hours.

            [ ] +1  approve
            [ ] +0  no opinion
            [ ] -1  disapprove (and reason why)
```

    1. Create a DISCUSS email thread on bval-dev@ for any vote questions, e.g.:

```text
            To: dev@bval.apache.org
            Subject: [DISCUSS] Apache BVal <version> Release Candidate

            Discussion thread for vote on <version> release candidate, with GIT source tag (r9999999).

            For more information on the release process, check out http://www.apache.org/dev/release.html .

            Some of the things to check before voting are:
            - does "mvn apache-rat:check" pass on the source
            - can you build the contents of source-release.zip and GIT tag
            - do all of the staged jars/zips contain the required LICENSE and NOTICE files
            - are all of the staged jars signed and the signature verifiable
            - is the signing key in the project's KEYS file and on a public server (i.e. http://www.apache.org/dist/bval/)
            - does the release pass the TCK
```

    1. Perform a review of the release and cast your vote. For more details
     on Apache releases see
     [http://www.apache.org/dev/release.html](http://www.apache.org/dev/release.html).
    1. A -1 vote does not necessarily mean that the vote must be redone,
however it is usually a good idea to rollback the release if a -1 vote is
received (see [Recovering from a vetoed release](#ReleaseProcess-RecoveringFromAVetoedRelease).
    1. After the vote has been open for at least 72 hours, has at least three
+1 PMC votes and no -1 votes, then post the results to the vote thread:
        1. Reply to the initial email prepending `[RESULT]` to the original subject
        1. Include a list of every binding +1, 0 or -1 vote.
        1. Example:

            The vote has passed with the following results:
            
            +1  
            name1 (binding)  
            name2 (binding)  
            name3 (binding)  
            name4 (non-binding)  
            
            I will proceed with the next steps.
            
            Best regards,  
            name

1. Finalizing a release
    1. Promote the staged nexus artifacts:
        1. [https://repository.apache.org/index.html](https://repository.apache.org/index.html)
        1. **Build Promotion --> Staging Repositories**
        1. Right click on the closed `org.apache.bval-XXX` staging repo and select **Release**.

    1. Update the generated portion of the website:
        1. `mvn site-deploy` from the tag checkout
        1. Remove staged site from https://dist.apache.org/repos/dist/dev/bval .

    1. Add the distribution artifacts to the distribution area:
        Move source archives staged to https://dist.apache.org/repos/dist/dev/bval/source to
        https://dist.apache.org/repos/dist/release/bval . Commit changes in both locations.

    1. Update the *Downloads* page of the website via the CMS to point to the new release artifacts:

```text
            http://www.apache.org/dyn/closer.cgi/bval/$  {project.version}/
            http://repo1.maven.org/maven2/org/apache/bval/$  {artifactId}/${project.version}/
```

    1. Update the [JIRA versions](https://issues.apache.org/jira/plugins/servlet/project-config/BVAL/versions)
     page to mark the version as **Released**, and set the date to the date that
     the release was approved. You may also need to make a new release entry for
     the next release.

1. Announcing the release
    1. After the mirrors have had time to update (24 hours to be on the safe
     side) update the wiki with pointers to the new release.
    1. Make an announcement about the release on the
     [bval-user](mailto:user@bval.apache.org),
     [bval-dev](mailto:dev@bval.apache.org), and
     [announce@apache.org](mailto:announce@apache.org) lists as per
     [the Apache Announcement Mailing Lists page](http://www.apache.org/foundation/mailinglists.html#foundation-announce])

```text
            To: user@bval.apache.org, dev@bval.apache.org, announce@apache.org
            Subject: [ANNOUNCEMENT] Apache BVal <version> Released

            The Apache BVal team is pleased to announce the release of:

            Apache BVal <version>

            Apache BVal delivers an implementation of the Java Bean Validation
            specification 2.0.  The following changes are included in this release:

            <changelist>

            Distribution packages can be downloaded from:
            http://bval.apache.org/downloads.html

            When downloading, please verify signatures using the KEYS file available at:
            http://www.apache.org/dist/bval/

            The release is also available in the central Maven repository:
            http://repo1.maven.org/maven2/org/apache/bval/

            The Apache BVal Team
```

<a name="ReleaseProcess-RecoveringFromAVetoedRelease"></a>
### Recovering from a vetoed release
1. Reply to the initial vote email prepending `[CANCELED]` to the original subject.

1. Rollback the version upgrades in trunk by *either*:
    1. Restore the 0.1-rc1.tar.gz and run

```sh
            mvn -Papache-release release:rollback
```

        , *or*:

    1. Manually revert the versions in trunk to the prior version and commit

1. Delete the git tag created by the `release:perform` step.

1. Drop the nexus staging repo:
    1. [https://repository.apache.org/index.html](https://repository.apache.org/index.html)
    1. **Enterprise --> Staging**
    1. **Staging tab --> Name column --> org.apache.bval**
    1. Right click on the closed `org.apache.bval-XXX` staging repo and select **Drop**.
1. Remove the staged site from the dev dist repo.
1. Make the required updates that caused the vote to be canceled.
1. Spin another release candidate!

<a name="ReleaseProcess-Verifyingreleasesignatures"></a>
### Verifying release signatures

On unix platforms the following command can be executed:

```sh
    for file in `find . -type f -iname '*.asc'`
    do
        gpg --verify $  {file} 
    done
```

You'll need to look at the output to ensure it contains only good signatures:

```text
    gpg: Good signature from ...
    gpg: Signature made ...
```

[Release Setup]: /release-setup.html
[repository FAQ]: http://people.apache.org/~henkp/repo/faq.html
[detached signatures]: http://www.apache.org/dev/release-signing.html#openpgp-ascii-detach-sig
