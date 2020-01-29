# Maven Cheat Sheet

### Get project version
```
mvn -q -Dexec.executable="echo" -Dexec.args='${project.version}' --non-recursive exec:exec
1.0.0-SNAPSHOT
```

### Run a single test case
```
mvn -Dtest=<file> test
```
Run a single test method
```
mvn -Dtest=TestClass#testMethod test
```
Debug tests -- tests will pause and await remote debugger on port 5005
```
mvn -Dtest=<file> -Dmaven.surefire.debug test
```
See [Maven - Debugging Tests](https://maven.apache.org/surefire/maven-surefire-plugin/examples/debugging.html)<br/>
See also: [How to run unit test with Maven](https://www.mkyong.com/maven/how-to-run-unit-test-with-maven/)

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

### Purge local Maven repository
```bash
mvn dependency:purge-local-repository
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

### Parallel Builds
1 thread per available CPU core
```bash
mvn -T 1C
```
[Your Maven build is slow. Speed it up!](https://jrebel.com/rebellabs/your-maven-build-is-slow-speed-it-up/)

### List Modules and Directories
Reactor Build Order
```
mvn validate
```

List modules by Artifact ID

**Note**: On Windows, use double quotes (`"`) in the `awk` statement
```
mvn --also-make dependency:tree | grep maven-dependency-plugin | awk '{ print $(NF-1) }'
```
This variant does not require `awk`. As above, use double quotes for Windows.
```
mvn -Dexec.executable='echo' -Dexec.args='${project.artifactId}' exec:exec -q
```

List Module Directories
```
mvn -q --also-make exec:exec -Dexec.executable="pwd"
```
1. [How to list active sub-modules in a Maven project?](https://stackoverflow.com/questions/3662291/how-to-list-active-sub-modules-in-a-maven-project)
1. [How to list the Maven build/compilation sequence based on dependencies?](https://stackoverflow.com/questions/21170453/how-to-list-the-maven-build-compilation-sequence-based-on-dependencies)
1. [Maven Tips and Tricks: Advanced Reactor Options](https://blog.sonatype.com/2009/10/maven-tips-and-tricks-advanced-reactor-options/)

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

### Generate Maven Project

```bash
mvn -B archetype:generate
    -DarchetypeGroupId=org.apache.maven.archetypes
    -DgroupId=com.log4j.maven
    -DartifactId=dependency-example
```
[Fix broken builds with this log4j Maven dependency example](https://www.theserverside.com/tutorial/Fix-broken-builds-with-this-log4j-Maven-dependency-example)

Quick Start

```bash
mvn archetype:generate \
    -DarchetypeGroupId=org.apache.maven.archetypes \
    -DarchetypeArtifactId=maven-archetype-quickstart
```

## Plugins

### Execute a specific plugin goal by ID
```bash
mvn sql:execute@create-db
```
See [Maven plugin execution ID](https://stackoverflow.com/a/33279426/6146580)<br/>
See also: [Run a single Maven plugin execution?](https://stackoverflow.com/a/28778436/6146580)z<br/>
See also: [SQL Maven Plugin#Executions](https://www.mojohaus.org/sql-maven-plugin/examples/execute.html)

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

## Maven Lifecycle

```
Lifecycle default -> [validate, initialize, generate-sources, process-sources, 
generate-resources, process-resources, compile, process-classes, generate-test-sources, 
process-test-sources, generate-test-resources, process-test-resources, test-compile, 
process-test-classes, test, prepare-package, package, pre-integration-test, integration-test, 
post-integration-test, verify, install, deploy]
[DEBUG] Lifecycle clean -> [pre-clean, clean, post-clean]
[DEBUG] Lifecycle site -> [pre-site, site, post-site, site-deploy]
```

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

See all: [Maven Command Line Options](https://books.sonatype.com/mvnref-book/reference/running-sect-options.html)

## References
1. [Maven - alternative .m2 directory](http://stackoverflow.com/a/16592061/6146580)
1. [How to Override the Maven Local Repository setting](https://confluence.atlassian.com/bamkb/how-to-override-the-maven-local-repository-setting-838546993.html)
1. Maven logging: [Maven logging and the command line](https://binkley.blogspot.com/2017/04/maven-logging-and-command-line.html) and [How to change maven logging level...](https://stackoverflow.com/a/19319402/6146580).
1. [Maven CLI Options Reference](https://maven.apache.org/ref/3.6.0/maven-embedder/cli.html)
1. [Purging local repository dependencies](https://maven.apache.org/plugins/maven-dependency-plugin/examples/purging-local-repository.html)
