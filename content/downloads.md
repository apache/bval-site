Title: Downloads

Apache BVal provides an implementation of the
[Jakarta Bean Validation][bv-spec] Specification
which is TCK compliant and works on Java SE 11 or later.

Apache BVal artifacts are distributed in source and binary form under the
terms of the [Apache License, Version 2.0][ALv2].
See the included `LICENSE` and `NOTICE` files included in each artifact for
additional license information.  Please read the
[Verifying Releases](#Downloads-VerifyingReleases) section below on
how to verify the integrity of downloaded files.

[bv-spec]: https://jakarta.ee/specifications/bean-validation/3.0/
[ALv2]: http://www.apache.org/licenses/LICENSE-2.0

### Current Releases

#### Apache BVal 3.0.2 - Java 11 - Jakarta Bean Validation 3.0 - Released March 15, 2025
Module | Artifact | Signatures | Comments
--|--|--|--
Source Distribution | [bval-parent-3.0.2-source-release.zip][src302] | [asc][src-asc302] [sha512][src-sha512302] | -
Jakarta Bean Validation 3.0 Implementation | [bval-jsr-3.0.2.jar][jsr302] | [asc][jsr-asc302] [md5][jsr-md5302] [sha1][jsr-sha1302] | `jakarta.validation.spi.ValidationProvider`
Implementation Bundle | [org.apache.bval.bundle-3.0.2.jar][bundle302] | [asc][bundle-asc302] [md5][bundle-md5302] [sha1][bundle-sha1302] | `jakarta.validation.spi.ValidationProvider` w/ OSGi metadata (includes `bval-jsr`)
Extra Routines and Constraints | [bval-extras-3.0.2.jar][bvextras302] | [asc][bvextras-asc302] [md5][bvextras-md5302] [sha1][bvextras-sha1302] | Optional module

[src302]: https://www.apache.org/dyn/closer.cgi/bval/bval-3.0.2/bval-parent-3.0.2-source-release.zip
[src-asc302]: https://www.apache.org/dist/bval/3.0.2/bval-parent-3.0.2-source-release.zip.asc
[src-sha512302]: https://www.apache.org/dist/bval/3.0.2/bval-parent-3.0.2-source-release.zip.sha512
[jsr302]: https://repo1.maven.org/maven2/org/apache/bval/bval-jsr/3.0.2/bval-jsr-3.0.2.jar
[jsr-asc302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/3.0.2/bval-jsr-3.0.2.jar.asc
[jsr-md5302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/3.0.2/bval-jsr-3.0.2.jar.md5
[jsr-sha1302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/3.0.2/bval-jsr-3.0.2.jar.sha1
[bundle302]: https://repo1.maven.org/maven2/org/apache/bval/org.apache.bval.bundle/3.0.2/org.apache.bval.bundle-3.0.2.jar
[bundle-asc302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/3.0.2/org.apache.bval.bundle-3.0.2.jar.asc
[bundle-md5302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/3.0.2/org.apache.bval.bundle-3.0.2.jar.md5
[bundle-sha1302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/3.0.2/org.apache.bval.bundle-3.0.2.jar.sha1
[bvextras302]: https://repo1.maven.org/maven2/org/apache/bval/bval-extras/3.0.2/bval-extras-3.0.2.jar
[bvextras-asc302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/3.0.2/bval-extras-3.0.2.jar.asc
[bvextras-md5302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/3.0.2/bval-extras-3.0.2.jar.md5
[bvextras-sha1302]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/3.0.2/bval-extras-3.0.2.jar.sha1

#### Apache BVal 2.0.6 - Java 8 - Bean Validation v2.0 - Released June 13 2022
Module | Artifact | Signatures | Comments
--|--|--|--
Source Distribution | [bval-parent-2.0.6-source-release.zip][src206] | [asc][src-asc206] [sha512][src-sha512206] | -
JSR380 Implementation | [bval-jsr-2.0.6.jar][jsr206] | [asc][jsr-asc206] [md5][jsr-md5206] [sha1][jsr-sha1206] | `javax.validation.spi.ValidationProvider`
Implementation Bundle | [org.apache.bval.bundle-2.0.6.jar][bundle206] | [asc][bundle-asc206] [md5][bundle-md5206] [sha1][bundle-sha1206] | `javax.validation.spi.ValidationProvider` w/ OSGi metadata (includes `bval-jsr`)
Extra Routines and Constraints | [bval-extras-2.0.6.jar][bvextras206] | [asc][bvextras-asc206] [md5][bvextras-md5206] [sha1][bvextras-sha1206] | Optional module

[src206]: http://www.apache.org/dyn/closer.cgi/bval/2.0.6/bval-parent-2.0.6-source-release.zip
[src-asc206]: http://www.apache.org/dist/bval/2.0.6/bval-parent-2.0.6-source-release.zip.asc
[src-sha512206]: http://www.apache.org/dist/bval/2.0.6/bval-parent-2.0.6-source-release.zip.sha512
[jsr206]: http://repo1.maven.org/maven2/org/apache/bval/bval-jsr/2.0.6/bval-jsr-2.0.6.jar
[jsr-asc206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/2.0.6/bval-jsr-2.0.6.jar.asc
[jsr-md5206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/2.0.6/bval-jsr-2.0.6.jar.md5
[jsr-sha1206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/2.0.6/bval-jsr-2.0.6.jar.sha1
[bundle206]: http://repo1.maven.org/maven2/org/apache/bval/org.apache.bval.bundle/2.0.6/org.apache.bval.bundle-2.0.6.jar
[bundle-asc206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/2.0.6/org.apache.bval.bundle-2.0.6.jar.asc
[bundle-md5206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/2.0.6/org.apache.bval.bundle-2.0.6.jar.md5
[bundle-sha1206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/2.0.6/org.apache.bval.bundle-2.0.6.jar.sha1
[bvextras206]: http://repo1.maven.org/maven2/org/apache/bval/bval-extras/2.0.6/bval-extras-2.0.6.jar
[bvextras-asc206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/2.0.6/bval-extras-2.0.6.jar.asc
[bvextras-md5206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/2.0.6/bval-extras-2.0.6.jar.md5
[bvextras-sha1206]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/2.0.6/bval-extras-2.0.6.jar.sha1

#### Apache BVal 1.1.2 - Java 6 - Bean Validation v1.1 - Released Nov 3 2016

Module | Artifact | Signatures | Comments
--|--|--|--
Source Distribution | [bval-parent-1.1.2-source-release.zip][src112] | [asc][src-asc112] [md5][src-md5112] [sha1][src-sha1112] | -
Core Framework | [bval-core-1.1.2.jar][core112] | [asc][core-asc112] [md5][core-md5112] [sha1][core-sha1112] | -
JSR349 Implementation | [bval-jsr-1.1.2.jar][jsr112] | [asc][jsr-asc112] [md5][jsr-md5112] [sha1][jsr-sha1112] | `javax.validation.spi.ValidationProvider` (requires `bval-core`)
Implementation Bundle | [org.apache.bval.bundle-1.1.2.jar][bundle112] | [asc][bundle-asc112] [md5][bundle-md5112] [sha1][bundle-sha1112] | `javax.validation.spi.ValidationProvider` w/ OSGi metadata (includes `bval-core` and `bval-jsr`)
Extra Routines and Constraints | [bval-extras-1.1.2.jar][bvextras112] | [asc][bvextras-asc112] [md5][bvextras-md5112] [sha1][bvextras-sha1112] | Optional module
Legacy Agimatec JSON support | [bval-json-1.1.2.jar][bvjson112] | [asc][bvjson-asc112] [md5][bvjson-md5112] [sha1][bvjson-sha1112] | Optional integration module
Legacy Agimatec XML support | [bval-xstream-1.1.2.jar][bvxstream112] | [asc][bvxstream-asc112] [md5][bvxstream-md5112] [sha1][bvxstream-sha1112] | Optional integration module

[src112]: http://www.apache.org/dyn/closer.cgi/bval/1.1.2/bval-parent-1.1.2-source-release.zip
[src-asc112]: http://www.apache.org/dist/bval/1.1.2/bval-parent-1.1.2-source-release.zip.asc
[src-md5112]: http://www.apache.org/dist/bval/1.1.2/bval-parent-1.1.2-source-release.zip.md5
[src-sha1112]: http://www.apache.org/dist/bval/1.1.2/bval-parent-1.1.2-source-release.zip.sha1
[core112]: http://repo1.maven.org/maven2/org/apache/bval/bval-core/1.1.2/bval-core-1.1.2.jar
[core-asc112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-core/1.1.2/bval-core-1.1.2.jar.asc
[core-md5112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-core/1.1.2/bval-core-1.1.2.jar.md5
[core-sha1112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-core/1.1.2/bval-core-1.1.2.jar.sha1
[jsr112]: http://repo1.maven.org/maven2/org/apache/bval/bval-jsr/1.1.2/bval-jsr-1.1.2.jar
[jsr-asc112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/1.1.2/bval-jsr-1.1.2.jar.asc
[jsr-md5112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/1.1.2/bval-jsr-1.1.2.jar.md5
[jsr-sha1112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr/1.1.2/bval-jsr-1.1.2.jar.sha1
[bundle112]: http://repo1.maven.org/maven2/org/apache/bval/org.apache.bval.bundle/1.1.2/org.apache.bval.bundle-1.1.2.jar
[bundle-asc112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/1.1.2/org.apache.bval.bundle-1.1.2.jar.asc
[bundle-md5112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/1.1.2/org.apache.bval.bundle-1.1.2.jar.md5
[bundle-sha1112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/1.1.2/org.apache.bval.bundle-1.1.2.jar.sha1
[bvextras112]: http://repo1.maven.org/maven2/org/apache/bval/bval-extras/1.1.2/bval-extras-1.1.2.jar
[bvextras-asc112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/1.1.2/bval-extras-1.1.2.jar.asc
[bvextras-md5112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/1.1.2/bval-extras-1.1.2.jar.md5
[bvextras-sha1112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/1.1.2/bval-extras-1.1.2.jar.sha1
[bvjson112]: http://repo1.maven.org/maven2/org/apache/bval/bval-json/1.1.2/bval-json-1.1.2.jar
[bvjson-asc112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-json/1.1.2/bval-json-1.1.2.jar.asc
[bvjson-md5112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-json/1.1.2/bval-json-1.1.2.jar.md5
[bvjson-sha1112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-json/1.1.2/bval-json-1.1.2.jar.sha1
[bvxstream112]: http://repo1.maven.org/maven2/org/apache/bval/bval-xstream/1.1.2/bval-xstream-1.1.2.jar
[bvxstream-asc112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-xstream/1.1.2/bval-xstream-1.1.2.jar.asc
[bvxstream-md5112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-xstream/1.1.2/bval-xstream-1.1.2.jar.md5
[bvxstream-sha1112]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-xstream/1.1.2/bval-xstream-1.1.2.jar.sha1

Note: this release depends on geronimo-validation_1.1_spec API jar or any official bean validation API. EL API is optional but enables new Bean Validation 1.1 features.

#### Apache BVal 0.5 - Java 5 - Bean Validation v1.0 - Released September 21, 2012

Module | Artifact | Signatures | Comments
--|--|--|--
Source Distribution | [bval-parent-0.5-source-release.zip][src] | [asc][src-asc] [md5][src-md5] [sha1][src-sha1] | -
Core Framework | [bval-core-0.5.jar][core] | [asc][core-asc] [md5][core-md5] [sha1][core-sha1] | -
JSR303 Implementation | [bval-jsr303-0.5.jar][jsr303] | [asc][jsr303-asc] [md5][jsr303-md5] [sha1][jsr303-sha1] | `javax.validation.spi.ValidationProvider` (requires `bval-core`)
Implementation Bundle | [org.apache.bval.bundle-0.5.jar][bundle] | [asc][bundle-asc] [md5][bundle-md5] [sha1][bundle-sha1] | `javax.validation.spi.ValidationProvider` w/ OSGi metadata (includes `bval-core` and `bval-jsr303`)
[Google Guice][guice] Integration | [bval-guice-0.5.jar][bvguice] | [asc][bvguice-asc] [md5][bvguice-md5] [sha1][bvguice-sha1] | Optional integration module
Extra Routines and Constraints | [bval-extras-0.5.jar][bvextras] | [asc][bvextras-asc] [md5][bvextras-md5] [sha1][bvextras-sha1] | Optional module
Legacy Agimatec JSON support | [bval-json-0.5.jar][bvjson] | [asc][bvjson-asc] [md5][bvjson-md5] [sha1][bvjson-sha1] | Optional integration module
Legacy Agimatec XML support | [bval-xstream-0.5.jar][bvxstream] | [asc][bvxstream-asc] [md5][bvxstream-md5] [sha1][bvxstream-sha1] | Optional integration module

[src]: http://www.apache.org/dyn/closer.cgi/bval/0.5/bval-parent-0.5-source-release.zip
[src-asc]: http://www.apache.org/dist/bval/0.5/bval-parent-0.5-source-release.zip.asc
[src-md5]: http://www.apache.org/dist/bval/0.5/bval-parent-0.5-source-release.zip.md5
[src-sha1]: http://www.apache.org/dist/bval/0.5/bval-parent-0.5-source-release.zip.sha1
[core]: http://repo1.maven.org/maven2/org/apache/bval/bval-core/0.5/bval-core-0.5.jar
[core-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-core/0.5/bval-core-0.5.jar.asc
[core-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-core/0.5/bval-core-0.5.jar.md5
[core-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-core/0.5/bval-core-0.5.jar.sha1
[jsr303]: http://repo1.maven.org/maven2/org/apache/bval/bval-jsr303/0.5/bval-jsr303-0.5.jar
[jsr303-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr303/0.5/bval-jsr303-0.5.jar.asc
[jsr303-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr303/0.5/bval-jsr303-0.5.jar.md5
[jsr303-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-jsr303/0.5/bval-jsr303-0.5.jar.sha1
[bundle]: http://repo1.maven.org/maven2/org/apache/bval/org.apache.bval.bundle/0.5/org.apache.bval.bundle-0.5.jar
[bundle-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/0.5/org.apache.bval.bundle-0.5.jar.asc
[bundle-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/0.5/org.apache.bval.bundle-0.5.jar.md5
[bundle-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/org.apache.bval.bundle/0.5/org.apache.bval.bundle-0.5.jar.sha1
[bvguice]: http://repo1.maven.org/maven2/org/apache/bval/bval-guice/0.5/bval-guice-0.5.jar
[bvguice-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-guice/0.5/bval-guice-0.5.jar.asc
[bvguice-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-guice/0.5/bval-guice-0.5.jar.md5
[bvguice-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-guice/0.5/bval-guice-0.5.jar.sha1
[bvextras]: http://repo1.maven.org/maven2/org/apache/bval/bval-extras/0.5/bval-extras-0.5.jar
[bvextras-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/0.5/bval-extras-0.5.jar.asc
[bvextras-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/0.5/bval-extras-0.5.jar.md5
[bvextras-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-extras/0.5/bval-extras-0.5.jar.sha1
[bvjson]: http://repo1.maven.org/maven2/org/apache/bval/bval-json/0.5/bval-json-0.5.jar
[bvjson-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-json/0.5/bval-json-0.5.jar.asc
[bvjson-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-json/0.5/bval-json-0.5.jar.md5
[bvjson-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-json/0.5/bval-json-0.5.jar.sha1
[bvxstream]: http://repo1.maven.org/maven2/org/apache/bval/bval-xstream/0.5/bval-xstream-0.5.jar
[bvxstream-asc]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-xstream/0.5/bval-xstream-0.5.jar.asc
[bvxstream-md5]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-xstream/0.5/bval-xstream-0.5.jar.md5
[bvxstream-sha1]: https://repository.apache.org/content/repositories/releases/org/apache/bval/bval-xstream/0.5/bval-xstream-0.5.jar.sha1

[guice]: http://code.google.com/p/google-guice/

<a name="Downloads-OlderReleases"></a>

### Older Releases

#### Apache BVal 1.1.0 - Released June 2015
Available at the [Apache release archive](http://archive.apache.org/dist/bval/1.1.0).

#### Apache BVal 0.4 - Released April 13, 2012
Available at the [Apache release archive](http://archive.apache.org/dist/bval/0.4).

#### Apache Bean Validation 0.3-incubating - Released April 28, 2011
Available at the [Apache release archive](http://archive.apache.org/dist/incubator/bval/0.3-incubating).

#### Apache Bean Validation 0.2-incubating - Released August 18, 2010
Available at the [Apache release archive](http://archive.apache.org/dist/incubator/bval/0.2-incubating).

#### Apache Bean Validation 0.1-incubating - Released June 11, 2010
Available at the [Apache release archive](http://archive.apache.org/dist/incubator/bval/0.1-incubating).

<a name="Downloads-MavenUsers"></a>
### Maven Users

Our artifacts are published to the Maven Central repository and can be
found under the `org.apache.bval` groupId.

You'll need to add the following dependencies in your builds (and Maven
will automatically include the additional transitive dependencies for you):

```html
<dependency>
  <groupId>org.apache.geronimo.specs</groupId>
  <artifactId>geronimo-validation_1.0_spec</artifactId>
  <version>1.1</version>
</dependency>
<dependency>
  <groupId>org.apache.bval</groupId>
  <artifactId>org.apache.bval.bundle</artifactId>
  <version>0.5</version>
</dependency>
```

Maven will determine the transitive dependencies for the artifacts, but if
you are not using Maven to build your project, then you will also need the
following dependencies on the classpath:

```html    
<dependency>
  <groupId>org.apache.commons</groupId>
  <artifactId>commons-lang3</artifactId>
  <version>3.1</version>
</dependency>
<dependency>
  <groupId>org.slf4j</groupId>
  <artifactId>slf4j-simple</artifactId>
  <version>1.6.1</version>
</dependency>
<dependency>
  <groupId>commons-beanutils</groupId>
  <artifactId>commons-beanutils</artifactId>
  <version>1.8.3</version>
</dependency>
```

<a name="Downloads-VerifyingReleases"></a>
### Verifying Releases

It is essential that you verify the integrity of any downloaded files using
the PGP or MD5 signatures.  For more information on signing artifacts and
why we do it, check out the
[Release Signing FAQ](http://www.apache.org/dev/release-signing.html).

The PGP signatures can be verified using PGP or GPG.  First download the [KEYS](http://www.apache.org/dist/bval/KEYS)
as well as the asc signature file for the artifact.  Make sure you get
these files from the
[main distribution directory](http://www.apache.org/dist/bval/),
rather than from a
[mirror](http://www.apache.org/dyn/closer.cgi/bval/).
Then verify the signatures using:

```sh
$ pgpk -a KEYS
$ pgpv bval-parent-0.5-source-release.zip.asc
```

or

```sh
$ pgp -ka KEYS
$ pgp bval-parent-0.5-source-release.zip.asc
```

or

```sh
$ gpg --import KEYS
$ gpg --verify bval-parent-0.5-source-release.zip.asc
```

Alternatively, you can verify the MD5 signature on the files. A Unix/Linux
program called `md5` or `md5sum` is included in most distributions.  It is
also available as part of
[GNU Textutils](http://www.gnu.org/software/textutils/textutils.html).
Windows users can get binary md5 programs from these (and likely other) places:

 * <http://www.md5summer.org/>
 * <http://www.fourmilab.ch/md5/>
 * <http://www.pc-tools.net/win32/md5sums/>
