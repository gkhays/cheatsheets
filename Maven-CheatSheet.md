# Maven Cheat Sheet

### Generate from archetype

```
mvn archetype:generate
```

For example to generate a Dropwizard poject.

```
mvn archetype:generate \
  -DarchetypeGroupId=io.dropwizard.archetypes \
  -DarchetypeArtifactId=java-simple \
  -DarchetypeVersion=4.0.8
```

There is also the JDK8 QuickStart.

```
mvn org.apache.maven.plugins:maven-archetype-plugin:3.1.2:generate \
  -DarchetypeArtifactId="archetype-quickstart-jdk8" \
  -DarchetypeGroupId="com.github.ngeor" \
  -DarchetypeVersion="2.8.1" \
  -DgroupId="com.example" \
  -DartifactId="demo"
```

<details>
  <summary>Results</summary>
 
```
[INFO] --- archetype:3.1.2:generate (default-cli) @ standalone-pom ---
[INFO] Generating project in Interactive mode
[INFO] Archetype repository not defined. Using the one from [com.github.ngeor:archetype-quickstart-jdk8:3.0.0] found in catalog remote
[INFO] Using property: groupId = com.example
[INFO] Using property: artifactId = demo
Define value for property 'version' 1.0-SNAPSHOT: :
[INFO] Using property: package = com.example
Confirm properties configuration:
groupId: com.example
artifactId: demo
version: 1.0-SNAPSHOT
package: com.example
 Y: :
[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Archetype: archetype-quickstart-jdk8:2.8.1
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: groupId, Value: com.example
[INFO] Parameter: artifactId, Value: demo
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] Parameter: package, Value: com.example
[INFO] Parameter: packageInPathFormat, Value: com/example
[INFO] Parameter: package, Value: com.example
[INFO] Parameter: groupId, Value: com.example
[INFO] Parameter: artifactId, Value: demo
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] Project created from Archetype in dir: D:\Users\ghays\poc\demo
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  01:18 min
[INFO] Finished at: 2024-09-19T16:37:28-05:00
[INFO] ------------------------------------------------------------------------
```
</details>

### Maven Configuration

`.mvn` directory:
Located within the project's top level directory, the files
- `maven.config`
- `jvm.config`
- `extensions.xml`

`.mvn/maven.config` file:
NOTICE starting with Maven 3.9.0 each single argument must be put on a new line, so for the mentioned example your file will have content like:
```
-T3
-U 
--fail-at-end
```

#### References
- [Configuring Apache Maven](https://maven.apache.org/configure.html)
- [Maven and Java](https://gist.github.com/LIttleAncientForestKami/46351176bc76538324f1809db0f2f79d)

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

### Property references

```
project.build.sourceDirectory
project.build.scriptSourceDirectory
project.build.testSourceDirectory
project.build.outputDirectory
project.build.testOutputDirectory
project.build.directory
```

See [Maven project.build.directory](https://stackoverflow.com/a/13354567/6146580)

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

Filter on a specific group ID.

```bash
mvn dependency:tree | grep -n -A 5 -B 20 "io.github"
```

### Analyze dependencies

```bash
mvn dependency:analyze
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

Alternatively

```bash
mvn -T 4 install -- will use 4 threads
mvn -T 2C install -- will use 2 threads per available CPU core
```

1. [Your Maven build is slow. Speed it up!](https://jrebel.com/rebellabs/your-maven-build-is-slow-speed-it-up/)
1. [How to Speed up Your Maven Build](https://www.jrebel.com/blog/how-to-speed-up-your-maven-build)

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

### Effective POM

```bash
mvn help:effective-pom
```

Or

```bash
mvn -q help:effective-pom -Deffective-pom.xml
```

[What are the difference between pom.xml and effective pom in Apache Maven?](https://stackoverflow.com/a/49736042/6146580)  
[Apache Maven Help Plugin](https://maven.apache.org/plugins/maven-help-plugin/effective-pom-mojo.html)  
[Maven Help Plugin Usage](https://maven.apache.org/plugins/maven-help-plugin/usage.html)

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

## Profiles

### Deactivate a Profile

```bash
mvn groupId:artifactId:goal -P !profile-1,!profile-2
```

With escape

```bash
mvn groupId:artifactId:goal -P \!profile-1
```

Or, as Shaun Morris suggested below, use - instead of !, but without whitespace between -P and the profiles:

```bash
mvn groupId:artifactId:goal -P-profile-1,-profile2
```

[De-activate a maven profile from command line](https://stackoverflow.com/a/25201551)

## Command Line Options

(Frequently used by me)

| Options                | Description                                                                                                                                                     |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -B,--batch-mode        | Run in non-interactive (batch) mode (disables output color)                                                                                                     |
| -D,--define            | Define a system property                                                                                                                                        |
| -e,--errors            | Produce execution error messages                                                                                                                                |
| -f,--file              | Force the use of an alternate POM file (or directory with pom.xml)                                                                                              |
| -N,--non-recursive     | Do not recurse into sub-projects                                                                                                                                |
| -o,--offline           | Work offline                                                                                                                                                    |
| -P,--activate-profiles | Comma-delimited list of profiles to activate                                                                                                                    |
| -pl,--projects         | Comma-delimited list of specified reactor projects to build instead of all projects. A project can be specified by [groupId]:artifactId or by its relative path |
| -rf,--resume-from      | Resume reactor from specified project                                                                                                                           |
| -s,--settings          | Alternate path for the user settings file                                                                                                                       |
| -U,--update-snapshots  | Forces a check for missing releases and updated snapshots on remote repositories                                                                                |
| -v,--version           | Display version information                                                                                                                                     |
| -X,--debug             | Produce execution debug output                                                                                                                                  |

See all: [Maven Command Line Options](https://books.sonatype.com/mvnref-book/reference/running-sect-options.html)

## References

1. [20+ Maven Commands and Options (Cheat Sheet)](https://www.digitalocean.com/community/tutorials/maven-commands-options-cheat-sheet)
1. [Maven - alternative .m2 directory](http://stackoverflow.com/a/16592061/6146580)
1. [How to Override the Maven Local Repository setting](https://confluence.atlassian.com/bamkb/how-to-override-the-maven-local-repository-setting-838546993.html)
1. [Maven CLI Options Reference](https://maven.apache.org/ref/3.6.0/maven-embedder/cli.html)
1. [Purging local repository dependencies](https://maven.apache.org/plugins/maven-dependency-plugin/examples/purging-local-repository.html)
1. [What are all of the Maven Command Line Options?](https://stackoverflow.com/a/47906431)
1. Maven logging: [Maven logging and the command line](https://binkley.blogspot.com/2017/04/maven-logging-and-command-line.html) and [How to change maven logging level...](https://stackoverflow.com/a/19319402/6146580)
1. [Maven Commands and Options](https://www.geeksforgeeks.org/maven-commands-and-options/)
1. [Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
