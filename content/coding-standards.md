Title: Coding Standards

## ASF Requirements

<a name="CodingStandards-Copyrightnoticesforsubmittedpatches"></a>
### Copyright notices for submitted patches

Please see <http://www.apache.org/legal/src-headers.html>
for details of the following summary.

Apache does not require you to assign ownership or copyright for any
patches that you submit via the above process. You retain ownership for all
such patches. But Apache does require you to grant Apache a license to use
the patch. To do this for new files, do not include a copyright statement
in the file but include this license as comments in the header of your
source contribution - <http://www.apache.org/legal/src-headers.html#headers>
If you require that distributions of the project include your copyright
notice, you should include with your patch an update to the NOTICE file at
`trunk/NOTICE.txt` documenting for which files you are notifying your copyright.

<a name="CodingStandards-LicenseandNoticefiles"></a>
### License and Notice files

Please see <http://www.apache.org/licenses/>
for details of the following summary.

All release artifacts published by an Apache project (JAR/WAR/EAR, zip,
tar, ...) must include License and Notice files.  A Disclaimer file must be
included for any artifacts included form the incubator.

<a name="CodingStandards-GeneralFormattingConventions"></a>
## General Formatting Conventions

We try to adhere to Sun's _Code Conventions for the Java Programming
Language_, which is available at <http://java.sun.com/docs/codeconv/>

1. Maximum line length is 120 characters (this is a deviation from the Java
standards of 80 chars).
1. Use spaces instead of tabs.
1. Indendation size is 4 spaces.
1. Do not insert a new line before opening brace. Insert a new line before
closing brace.
1. Use fully qualified import statements, i.e. do not use asterisks.

<a name="CodingStandards-EclipseUsers"></a>
## Eclipse Users

<a name="CodingStandards-FormatterProfile"></a>
### Formatter Profile
Download the code formatter profile: 
[bval-formatting-preferences.xml](/coding/bval-formatting-preferences.xml)

Updated profile for Eclipse Galileo: [bval-eclipse-galileo-formatting.xml](/coding/bval-eclipse-galileo-formatting.xml)

To import:

1. **Window -> Preferences**
1. **Java -> Code Style -> Formatter**
1. Click on import and select the file downloaded above.
1. Press **OK** after importing

<a name="CodingStandards-CodeTemplate"></a>
### Code Template
Download the code template profile: 
[bval-code-style-template.xml](/coding/bval-code-style-template.xml)

To import:

1. **Window -> Preferences**
1. **Java -> Code Style -> Code Templates**
1. Click on import and select the file downloaded above.
1. Press **OK** after importing

<a name="CodingStandards-SubmittingaPatch"></a>
## Submitting a Patch

If you make changes to BVal, and would like to contribute them to the
project, you should create a patch via svn and post it to the [BVal JIRA issue tracker](http://issues.apache.org/jira/browse/BVAL).
To create a patch, simply execute the following command:

    svn diff > your-changes.patch

*Note:* You may also use Eclipse to create a patch (**Team -> Create
Patch...**), but this may require committers to modify the patch to match
their project layout (workspace per branch or all branches in one
workspace) and some committers may not be using Eclipse/Subclipse.

<a name="CodingStandards-TestCases"></a>
## TestCases

When we make a change or introduce a new feature, it's generally good
practice to include a [JUnit][] testcase which demonstrates the desired
behavior.

The testcase should be self validating via JUnit assertions. Writing messages
to `System.err` or `System.out` or extraneous logging is discouraged; they
lead to the impression that some manual interpretation of the results must
be done. Messages like these are useful when developing the tests or when
diagnosing problems but should either be included as `TRACE` level logging or
not be committed.

[junit]: http://junit.org
