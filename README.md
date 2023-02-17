# CheckStyle

Util artifact for importing checkstyle settings and suppressions

## Usage

In the base project `pom.xml`:

* Add checkstyle properties

```xml

<properties>
  <!-- checkstyle -->
  <checkstyle.config.location>checkstyle.xml</checkstyle.config.location>
  <checkstyle.suppressions.location>suppressions.xml</checkstyle.suppressions.location>

  <!-- versions -->
  <maven.checkstyle.version>3.2.0</maven.checkstyle.version>
  <checkstyle.version>0.0.3</checkstyle.version>
</properties>
```

* Add maven checkstyle plugin config, with this artifact as a dependency

```xml

<build>
  <pluginManagement>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <version>${maven.checkstyle.version}</version>
        <dependencies>
          <dependency>
            <groupId>io.github.aj8gh</groupId>
            <artifactId>checkstyle</artifactId>
            <version>${checkstyle.version}</version>
          </dependency>
        </dependencies>
        <executions>
          <execution>
            <id>validate</id>
            <phase>validate</phase>
            <goals>
              <goal>check</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </pluginManagement>

  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-checkstyle-plugin</artifactId>
    </plugin>
  </plugins>
</build>
```
