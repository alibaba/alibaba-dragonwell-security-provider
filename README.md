Alibaba Dragonwell Security Provider - A Java Security Provider
========================================

Alibaba Dragonwell Security Provider is a Java Security Provider (JSP) that
implements parts of the Java Cryptography Extension (JCE) and Java Secure
Socket Extension (JSSE).  It uses Tongsuo to provide cryptographic primitives
and Transport Layer Security (TLS) for Java applications on Dragonwell JDK.
See [the capabilities documentation](CAPABILITIES.md) for detailed information
on what is provided. Except that, Alibaba Dragonwell Security Provider supports
TLCP protocal and SM2/SM3/SM4 encryption algorithm.

The core SSL engine has borrowed liberally from the [Netty](http://netty.io/)
project and their work on [netty-tcnative](http://netty.io/wiki/forked-tomcat-native.html),
giving `Tongsuo` similar performance.


Download
-------------
Alibaba Dragonwell Security Provider supports **Java 8** or **Java 11** on Dragonwell JDK.
The build artifacts are available on Maven Central.

### Download JARs
You can download
[the JARs](http://search.maven.org/#search%7Cga%7C1%7Cg:%22net.tongsuo%22)
directly from the Maven repositories.

### OpenJDK (i.e. non-Android)

#### Native Classifiers

The OpenJDK artifacts are platform-dependent since each embeds a native library for a particular
platform. We publish artifacts to Maven Central for the following platforms:

| Classifier     |  OS   | Architecture    |
|----------------|-------|-----------------|
| linux-x86_64   | Linux | x86_64 (64-bit) |



#### Maven

Use the [os-maven-plugin](https://github.com/trustin/os-maven-plugin) to add the dependency:

```xml
<dependency>
  <groupId>com.alibaba.dragonwell.security</groupId>
  <artifactId>native-openssl</artifactId>
  <version>1.0.0</version>
  <classifier>${os.detected.classifier}</classifier>
</dependency>
```

#### Gradle
Use the [osdetector-gradle-plugin](https://github.com/google/osdetector-gradle-plugin)
(which is a wrapper around the os-maven-plugin) to add the dependency:

```gradle
buildscript {
  repositories {
    mavenCentral()
  }
  dependencies {
    classpath 'com.google.gradle:osdetector-gradle-plugin:1.4.0'
  }
}

// Use the osdetector-gradle-plugin
apply plugin: "com.google.osdetector"

dependencies {
  compile 'com.alibaba.dragonwell.security:native-openssl:1.0.0:' + osdetector.classifier
}
```

How to Build
------------

If you are making changes to Alibaba Dragonwell Security Provider, see the [building instructions](BUILDING.md).
