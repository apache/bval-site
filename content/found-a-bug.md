Title: Found a Bug

<a name="FoundaBug-FoundaBug?"></a>
## Found a Bug?

If you think you've found a problem with Apache BVal, there are several
ways to proceed.

You can begin by raising the issue on our User or Developer mailing lists
(see [Mailing Lists](mailing-lists.html)).

You can also search JIRA, our issue-tracking system, to see if the problem
has already been noted
(visit [JIRA](http://issues.apache.org/jira/browse/BVAL)).
If the issue is not listed there, you can add a new JIRA issue
describing it. Please include detailed steps to reproduce the problem,
including the Version Info.

If you have a fix for the issue, you can generate a patch file to send the
fix to us. You need to check out the current source code from Subversion
(see [Source Code](/source-code.html)),
make the necessary changes (see [Coding Standards](/coding-standards.html)),
and then do a full build with all tests enabled
(see [Building](/building.html))
and make sure the unit tests runs as expected (try `maven clean install`
to run a full build), and of course, confirm that the problem is
actually fixed. Then, go to the root directory of your BVAL checkout, and
run a command like `svn diff > BVAL-[JIRA_NUMBER].patch.txt` to generate a
patch file.

To submit a patch, create an issue in JIRA that describes the problem, add
your patch file as an attachment (don't forget to select the "Grant license
to ASF for inclusion in ASF works" option), and then edit the JIRA issue to
select the Patch Available check box.  Please include detailed steps to
reproduce the problem in the issue description, and a test case in the
patch where possible.

For larger contributions, like new features or more complex bug fixes, you
should also have an
[Individual Contributor License Agreement](http://www.apache.org/licenses/#clas)
on file with the ASF.

Thanks for working with us to improve Apache BVal!

<a name="FoundaBug-ReportingSecurityVulnerabilities"></a>
## Reporting Security Vulnerabilities

The Apache Software Foundation takes a very active stance in eliminating
security problems and denial of service attacks against the code we
provide.

We strongly encourage folks to report any such problems discovered in
Apache BVal to our private PMC mailing list <private@bval.apache.org>
first, before disclosing them in a public forum.

Please note that the private PMC mailing list should only be used for
reporting undisclosed security vulnerabilities and managing the process of
fixing such vulnerabilities until they are made public. We will not accept
regular bug reports or other general user queries at this address.

If you need to report a bug that is already a disclosed security
vulnerability, please use the regular bug reporting process above.

Questions about:

* how to securely configure BVal
* if a vulnerability applies to your particular application or Bean
Validation level
* obtaining further information on a published vulnerability
* availability of patches and/or new releases

should be addressed to the users mailing list. Please see the [Mailing Lists](mailing-lists.html)
 page for details of how to subscribe.
