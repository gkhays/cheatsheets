# Maven Cheat Sheet

### Remove platform encoding warning
```xml
<project ...>
 ...
 <properties>
   <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
   ...
 </properties>
 ..
</project>
```

### Get a dependency tree
```bash
mvn dependency:tree
```

### Override local repository
```bash
mvn -Dmaven.repo.local=/build/.m2/repository
```

### Custom User settings file
```bash
-s,--settings <arg> e.g.

mvn -s ~/custom/settings.xml
```

### Use global settings file
```bash
-gs,--global-settings <arg> e.g.

mvn -gs /build/settings.xml
```

### Force Update from Remote Repository
```bash
-U,--update-snapshots e.g.

mvn -U
```

### Log File
**Note**: Suppresses output to the console.
```bash
-l,--log-file <arg> e.g.

mvn -l maven.log
```

## Plugins

### Shade or Uber JAR

Automatically remove classes not being used.

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-shade-plugin</artifactId>
        <version>3.1.0</version>
        <executions>
          <execution>
            <phase>package</phase>
            <goals>
              <goal>shade</goal>
            </goals>
            <configuration>
              <minimizeJar>true</minimizeJar>
            </configuration>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

See [Selecting Contents for Uber JAR](https://maven.apache.org/plugins/maven-shade-plugin/examples/includes-excludes.html).

## References
1. [Maven - alternative .m2 directory](http://stackoverflow.com/a/16592061/6146580)
2. [How to Override the Maven Local Repository setting](https://confluence.atlassian.com/bamkb/how-to-override-the-maven-local-repository-setting-838546993.html)
