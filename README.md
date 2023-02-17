# CheckStyle

Util artifact for importing checkstyle settings and suppressions

## Usage

In the base project `pom.xml`:

* Add checkstyle properties

```xml

<properties>
  <!-- checkstyle -->
  <checkstyle.config.location>google_checks.xml</checkstyle.config.location>
  <checkstyle.severity>warning</checkstyle.severity>
  <checkstyle.fail>true</checkstyle.fail>
  <checkstyle.console>true</checkstyle.console>

  <!-- versions -->
  <maven.checkstyle.version>3.2.0</maven.checkstyle.version>
  <checkstyle.version>1.0.0</checkstyle.version>
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
        <configuration>
          <configLocation>${checkstyle.config.location}</configLocation>
          <violationSeverity>${checkstyle.severity}</violationSeverity>
          <failOnViolation>${checkstyle.fail}</failOnViolation>
          <consoleOutput>${checkstyle.console}</consoleOutput>
          <suppressionsLocation>checkstyle-suppressions.xml</suppressionsLocation>
        </configuration>
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
