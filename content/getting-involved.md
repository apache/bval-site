Title: Getting Involved

<a name="GettingInvolved-JointheApacheBValCommunity"></a>
## Join the Apache BVal Community

The Apache BVal project is being built by the open source community for the
open source community - we welcome your input and contributions!

<a name="GettingInvolved-Whatwearelookingfor"></a>
### What we are looking for

 * Source code and fixes contributions
 * Test cases for issues encountered during application development 
 * Documentation assistance
 * Product and feature suggestions
 * Detailed and constructive feedback
 * Articles and whitepapers

<a name="GettingInvolved-HowdoIContribute?"></a>
### How do I Contribute?

 * To discuss Apache BVal topics check out the [mailing lists](mailing-lists.html)
.
 * Bugs and other issues can be posted on the project [JIRA](http://issues.apache.org/jira/browse/BVAL)
.

<a name="GettingInvolved-IhaveencounteredanissuewithApacheBVal.WhatdoIdonow?"></a>
### I have encountered an issue with Apache BVal. What do I do now?

  * Post a message to our User's list to discuss the issue.
  * Search existing [JIRA issues](http://issues.apache.org/jira/browse/BVAL)
 to see whether someone has already encountered the same issue.
  * If this issue has never been encountered before, create a [JIRA issue](http://issues.apache.org/jira/browse/BVAL)
.
  * Develop a test case to demonstrate the issue. 
  * Attach the new test to JIRA issue. 
  * Check out the [Found a Bug](found-a-bug.html)
 page for more details on creating and submitting patches.

### I have encountered an issue with Apache BVal and have fixed it in the source code. How do I get the changes into svn?

 * Create a [JIRA issue](http://issues.apache.org/jira/browse/BVAL)
 that describes the changes you've made (you'll need an Apache JIRA account
to do this).
 * Check out the source code and make your changes. 
 * Create test cases to validate your changes.
 * `svn add` any new files.
 * Run `mvn test -Dtest=[MyTestCase]` to validate your change. You need
to specify the test to run by its simple name without package name.
 * Run the an entire build with tests by running `mvn clean install`
for any possible regression. This should take 2-5 minutes or so.
 * Check out the [Found a Bug](found-a-bug.html)
 page for more details on creating and submitting patches.
 * Wait for a committer to review and check in your changes.

