Title: Building

<a name="Building-Java"></a>
## Java

You will need a recent version of Java SE 5 or later installed to build and run the JUnit tests.

Apache BVal supports the Oracle (formerly Sun) JDK available at <http://java.oracle.com>.
The IBM Java SDK at <http://www.ibm.com/developerworks/java/jdk/> should also work and will be supported as well as possible.
Other Java vendors or versions may work, so please ping the [Mailing Lists](/mailing-lists.html) if you encounter problems. We will aim for across-the-board compatibility wherever possible.

<a name="Building-Maven"></a>
## Maven

<a name="Building-CommandLineBuilds"></a>
### Command Line Builds

These instructions describe how to check out the current BVal trunk source
code from the Apache Software Foundation's [Apache Subversion][svn]
source code management repository and build it using the
[Apache Maven][mvn] build tool.
These utilities support use from the console and are known to work on Windows, Linux and Mac OS X.

1. Ensure that you have Java installed and in your path by running:
 `java -version`
1. Install Apache Maven, version 2.2.1 or later. If it is installed correctly,
 typing `mvn -v` from the console will display the expected version number.
1. Install Apache Subversion v1.4.x or later.
If it installed correctly, typing the following command should output help
information: `svn help` or `svn --version`
1. Create a new directory you want to do your work in, then change to that
directory from the console.
1. Check out the sources by running: `svn co
http://svn.apache.org/repos/asf/bval/trunk bval-trunk`. It will
check out the sources to a `bval-trunk` directory (ASF committers use `https`).
1. Change to the `bval-trunk` directory, which has already been created in
the previous step.
1. Build the code by running: `mvn install`. The first time you run the
build, many dependencies are automatically resolved and downloaded. *It is
common for dependency downloading to fail the first time, which will fail
the build.* If any of these dependency downloads fail, just re-run the
command. You may also want to add a maven central mirror repository to your
`~/.m2/settings.xml` file if download times are consistently slow or fail
(see [here](http://maven.apache.org/guides/mini/guide-mirror-settings.html)).

<a name="Building-EclipsewithCommand-lineMavenutilities"></a>
## Eclipse with Command-line Maven utilities

1. Checkout the source as described above
1. Build the source using Maven as described above

   ```sh
   mvn eclipse:eclipse
   ```

   If this is the first project in your workspace to use maven artifacts you need to create a classpath variable named M2_REPO which contains the full path to your local repository. The eclipse plugin can do this for you with the following command:

   ```sh
   mvn eclipse:configure-workspace -Declipse.workspace=$  {path_to_your_workspace}
   ```

1. Start Eclipse (3.4 or later suggested) and create a new workspace
1. Import the BVal project, by:

    * Select File --> Import... --> General - Existing Projects into Workspace
--> Next
    * Select root directory = *[svn checkout location above]*
    * Press Finish

<a name="Building-EclipsewithM2Eclipseplugin"></a>
## Eclipse with M2Eclipse plugin

1. Checkout the source as described above
1. Build the source using Maven as described above
1. Start Eclipse (3.5 Galileo or later is recommended)
 and create a new workspace
1. Good references for this M2Eclipse plugin (need to install the plugin
into your Eclipse environment)
    * <http://m2eclipse.codehaus.org/>
    * <http://docs.codehaus.org/display/M2ECLIPSE/Home>
    * <http://www.theserverside.com/tt/articles/article.tss?l=Introductiontom2eclipse>
1. Import the BVAL project, by:
    * Select **File --> Import... --> General -> Maven Projects --> Next**
    * Select root directory = *[svn checkout location above]*
    * All of the `pom.xml` files should be pre-selected for the `svn` checkout
location
    * You can affect the naming convention used for the generated Eclipse projects (one for each Maven module).  Click on **Advanced** and fill in the **Name Template** field.  I prefer **TRUNK-**_artifactId_ since it helps with workspace organization, but it's your choice.
    * Press Finish
    * *Note:*  You may get a popup internal error at the end of this Import
processing.  Not sure what the problem is, but it doesn't seem to affect
the usage.  This will probably get cleared up soon since Eclipse 3.5 is
still quite new.
    * `The bval-jsr303` module needs the `jaxb2:xjc` goal to run as part of its
build process:	Add this to the project's **Maven --> Lifecycle Mapping**
options under **Goals to invoke after project clean:**.

[svn]: http://subversion.apache.org
[mvn]: http://maven.apache.org
