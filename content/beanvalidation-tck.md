Title: JSR303 TCK

<a name="JSR303TCK-HowtoobtaintheTCKfortesting"></a>
### How to obtain the TCK for testing

The Bean Validation TCK was created by [Red Hat/JBoss][jboss] and is
available under the [Apache License, version 2.0][ALv2], which allows anyone
to download and run the TCK without having to sign the Sun/ASF NDA.

Please see the
[Bean Validation TCK](http://community.jboss.org/wiki/BeanValidationTCK)
website for details on how to setup a local JBoss instance for running the TCK.
The `bval-tck11` module should be used to execute the TCK against Apache BVal.

### Steps to run the TCK

For the below build and TCK runs, it is assumed that you have the latest Sun
1.6.0 JDK installed and set as the default Java implementation.

#### Standalone

1. Build the project and run the [JUnit][] tests:

   ```sh
   cd bval/trunk
   mvn clean install
   ```

1. Run the JBoss provided TCK in standalone mode -

   ```sh
   cd bval/trunk/bval-tck11
   mvn -Ptck
   ```

#### In-container

1. Build the project and run the [JUnit][] tests:

   ```sh
   cd bval/trunk
   mvn clean install
   ```

1. Install [JBoss Application Server](http://www.jboss.org/jbossas); version
   5.1.0 or later.
1. Run the JBoss provided TCK in the in-container mode, against your JBoss AS
   installation (where `$jbosshome` denotes the installation path):

   ```sh
   cd bval/trunk/bval-tck
   mvn -Ptck,incontainer -Djboss.home=$jbosshome
   ```

### Certification against the JCP provided TCK

*TBD* - Must we use the Sun/Oracle provided TCK for final certification testing?

[ALv2]: http://www.apache.org/licenses/LICENSE-2.0
[junit]: http://junit.org
[jboss]: http://www.jboss.org/
