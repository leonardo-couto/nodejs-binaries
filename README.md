nodejs-binaries
===============

Node.js Linux and MacOS binaries as a Maven dependency.

**Usage**

In your pom add the following properties and dependency.

```xml
  <project>
    ...
    <properties>
      ...
      <node.os>linux</node.os>
      <node.arch>x86</node.arch>
    </properties>
    
    <dependencies>
      ...
      <dependency>
        <groupId>com.github.leonardo-couto</groupId>
        <artifactId>nodejs-binaries</artifactId>
        <version>10.0.28.1</version>
        <classifier>${node.os}-${node.arch}</classifier>
        <type>tar.gz</type>
      </dependency>
    </dependencies>
  </project>
```
Possible values supported for OS (*node.os*) are *linux* and *macos*. For architecture (*node.arch*) values *x86* and *x64* are valid.

Typical usage let Maven choose the package based on user operational system and architecture through Maven profile activation.

```xml
  <profiles>
    <profile>
      <id>x64</id>
      <activation>
        <os>
          <arch>x64</arch>
        </os>
      </activation>
      <properties>
        <node.arch>x64</node.arch>
      </properties>
    </profile>
    <profile>
      <id>mac</id>
      <activation>
        <os>
          <family>mac</family>
        </os>
      </activation>
      <properties>
        <node.os>macos</node.os>
      </properties>
    </profile>
    ...
```


