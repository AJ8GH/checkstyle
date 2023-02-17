# CheckStyle

Util artifact for importing checkstyle settings and suppressions


May need the following for multi-module projects:

```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-dependency-plugin</artifactId>
  <version>${maven.dependency.version}</version>
  <executions>
    <execution>
      <phase>generate-sources</phase>
      <goals>
        <goal>unpack</goal>
      </goals>
      <configuration>
        <artifactItems>
          <artifactItem>
            <groupId>io.github.aj8gh</groupId>
            <artifactId>util</artifactId>
            <version>${project.parent.version}</version>
            <type>jar</type>
            <overWrite>false</overWrite>
            <includes>**/checkstyle-suppressions.xml</includes>
            <outputDirectory>${project.build.directory}/classes</outputDirectory>
          </artifactItem>
        </artifactItems>
      </configuration>
    </execution>
  </executions>
</plugin>
```

```shell
mvn install:install-file \
-DgroupId=io.github.aj8gh \
-DartifactId=checkstyle \
-Dversion=1.0.0 \
-Dfile=<jar-file> \
-Dpackaging=jar \
-DgeneratePom=true \
-DlocalRepositoryPath=. \
-DcreateChecksum=true
```
