Title: Version Info

### Command-line

To determine the Apache BVal version and revision you are using, run the
following command from a cmdline:

    java -jar ./bval-core-0.1-incubating-SNAPSHOT.jar

Which should display the project version, svn revision and your local
runtime environment, like:

    Project: Apache BVal
    Version: 0.1-incubating-SNAPSHOT
    Revision: 943245
    
    os.name: Mac OS X
    os.version: 10.6.3
    os.arch: x86_64
    
    java.version: 1.6.0_17
    java.vendor: Apple Inc.
    
    java.class.path:
    	./bval-core-0.1-incubating-SNAPSHOT.jar
    
    user.dir: /Users/xxxxx/validation/apache-bval/trunk/bval-core/target



<a name="VersionInfo-Programmatic"></a>
### Programmatic

For programmatic access, take a look at the public getters in:

    bval-core/src/main/java/org/apache/bval/util/BValVersion.java

including the following, which will return the strings above:

    getName() == "Apache BVal"
    getVersion() == "0.1-incubating-SNAPSHOT"
    getRevision() == "943245"


