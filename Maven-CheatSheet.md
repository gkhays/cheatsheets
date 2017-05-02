# Maven Cheat Sheet

### Override local repository
```bash
mvn -Dmaven.repo.local=/build/.m2/repository
```

### Use custom settings file
```bash
mvn -s ~/custom/settings.xml
```

### Use global settings file
```bash
mvn -gs /build/settings.xml
```

## References
1. [Maven - alternative .m2 directory](http://stackoverflow.com/a/16592061/6146580)
2. [How to Override the Maven Local Repository setting](https://confluence.atlassian.com/bamkb/how-to-override-the-maven-local-repository-setting-838546993.html)
