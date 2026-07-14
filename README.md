# jpms-maven-resolver-transport-http
The jpms-maven-resolver-transport-http repository is dedicated to making the `maven-resolver-transport-http` module from the [Apache Maven Resolver](https://github.com/apache/maven-resolver) project compliant with the Java Platform Module System (JPMS). This compliance ensures that the library can be seamlessly integrated into modular Java applications, leveraging the benefits of JPMS such as improved encapsulation, security, and maintainability.

## Features

* **JPMS Compliance:** The library is packaged as a JPMS module, enabling better encapsulation and dependency management in Java projects.
* **Ease of Use:** Simple integration into projects using JPMS.

## Known Caveat: Wrapping an Alpha Upstream Release

Unlike most `jpms-*` wrappers in this org, `maven-resolver-transport-http` has **never reached a GA release** in the Maven Resolver 2.x line — the latest available coordinates on Maven Central are still `2.0.0-alpha-2` (confirmed via Central's repository metadata). This wrapper repackages that alpha artifact as-is.

`maven-resolver-transport-http` is nonetheless required because it is the only artifact in the Resolver 2.x line that performs HTTP-based remote Maven repository access, and downstream consumers that ship via `jlink` (which refuses automatic modules anywhere in the linked module graph) need a real `module-info` for it. Reviewers should treat the alpha status of the upstream artifact as a known maturity caveat, and re-evaluate this wrapper once/if upstream cuts a GA release of `transport-http`.

## Getting Started
### Prerequisites

* **Java 11 or higher:** JPMS was introduced in Java 9, so a minimum of Java 11 is recommended for compatibility and support.
* **Maven or Gradle:** For dependency management and building the project.

Add the following dependency to your pom.xml:
```xml
<dependency>
    <groupId>dev.ikm.jpms</groupId>
	<artifactId>maven-resolver-transport-http</artifactId>
    <version>${latest-jpms-maven-resolver-transport-http-version}</version>
</dependency>
```

Add the following dependency to your build.gradle:
```groovy
implementation 'dev.ikm.jpms:maven-resolver-transport-http:${latest-jpms-maven-resolver-transport-http-version}'
```

In your module descriptor (module-info.java), declare the dependency on the jpms-maven-resolver-transport-http module:

```java
module your.module.name {
    requires dev.ikm.jpms.maven.resolver.transport.http;
}
```

## Dependencies

This wrapper depends on sibling JPMS wrapper modules published from this same org:

* `dev.ikm.jpms:httpclient4` ([jpms-httpclient4](https://github.com/ikmdev/jpms-httpclient4))
* `dev.ikm.jpms:httpcore4` ([jpms-httpcore4](https://github.com/ikmdev/jpms-httpcore4))
* `dev.ikm.jpms:commons-codec` ([jpms-commons-codec](https://github.com/ikmdev/jpms-commons-codec))
* `dev.ikm.jpms:jcl-over-slf4j` ([jpms-jcl-over-slf4j](https://github.com/ikmdev/jpms-jcl-over-slf4j))

## Issues and Contributions
Technical and non-technical issues can be reported to the [Issue Tracker](https://github.com/ikmdev/jpms-maven-resolver-transport-http/issues).

Contributions can be submitted via pull requests. Please check the [contribution guide](doc/how-to-contribute.md) for more details.
