# Maven Cheat Sheet

### Get project version
```
mvn -q -Dexec.executable="echo" -Dexec.args='${project.version}' --non-recursive exec:exec
1.0.0-SNAPSHOT
```

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

### Logging Level
```bash
mvn clean package -Dorg.slf4j.simpleLogger.defaultLogLevel=DEBUG
```
Alternatively, you can edit it in `${MAVEN_HOME}/conf/logging/simplelogger.properties` or by creating `.mvn/jvm.config`.

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

### Batch Mode
```bash
mvn -B
```
[Maven Command Line Options](https://books.sonatype.com/mvnref-book/reference/running-sect-options.html)

### Local Dependencies

```xml
<dependency>
    <groupId>com.sample</groupId>
    <artifactId>sample</artifactId>
    <version>1.0</version>
    <scope>system</scope>
    <systemPath>${project.basedir}/src/main/resources/yourJar.jar</systemPath>
</dependency>
```

See [How to add local jar files to a Maven project?](https://stackoverflow.com/a/22300875).

Alternatively

```bash
mvn install:install-file
   -Dfile=<path-to-file>
   -DgroupId=<group-id>
   -DartifactId=<artifact-id>
   -Dversion=<version>
   -Dpackaging=<packaging>
   -DgeneratePom=true

Where: <path-to-file>  the path to the file to load
   <group-id>      the group that the file should be registered under
   <artifact-id>   the artifact name for the file
   <version>       the version of the file
   <packaging>     the packaging of the file e.g. jar
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

### Release Plugin

```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-release-plugin</artifactId>
  <version>2.5.3</version>
  <configuration>
    <tagNameFormat>v@{project.version}</tagNameFormat>
  </configuration>
</plugin>
```
[Maven Release Plugin > Prepare a Release](https://maven.apache.org/maven-release/maven-release-plugin/examples/prepare-release.html)

## Command Line Options
(Frequently used by me)
| Options                | Description            |
|------------------------|------------------------|
| -B,--batch-mode        | Run in non-interactive (batch) mode (disables output color) |
| -D,--define            | Define a system property |
| -e,--errors            | Produce execution error messages |
| -f,--file              | Force the use of an alternate POM file (or directory with pom.xml) |
| -N,--non-recursive     | Do not recurse into sub-projects |
| -o,--offline           | Work offline |
| -P,--activate-profiles | Comma-delimited list of profiles to activate |
| -pl,--projects         | Comma-delimited list of specified reactor projects to build instead of all projects. A project can be specified by [groupId]:artifactId or by its relative path |
| -rf,--resume-from      | Resume reactor from specified project |
| -s,--settings          | Alternate path for the user settings file |
| -U,--update-snapshots  | Forces a check for missing releases and updated snapshots on remote repositories |
| -v,--version           | Display version information |
| -X,--debug             | Produce execution debug output |

## References
1. [Maven - alternative .m2 directory](http://stackoverflow.com/a/16592061/6146580)
2. [How to Override the Maven Local Repository setting](https://confluence.atlassian.com/bamkb/how-to-override-the-maven-local-repository-setting-838546993.html)
3. Maven logging: [Maven logging and the command line](https://binkley.blogspot.com/2017/04/maven-logging-and-command-line.html) and [How to change maven logging level...](https://stackoverflow.com/a/19319402/6146580).
4. [Maven CLI Options Reference](https://maven.apache.org/ref/3.6.0/maven-embedder/cli.html)
