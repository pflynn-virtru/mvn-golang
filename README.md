[![License Apache 2.0](https://img.shields.io/badge/license-Apache%20License%202.0-green.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Java 6.0+](https://img.shields.io/badge/java-6.0%2b-green.svg)](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[![Maven central](https://maven-badges.herokuapp.com/maven-central/com.igormaznitsa/mvn-golang-builder/badge.svg)](http://search.maven.org/#artifactdetails|com.igormaznitsa|mvn-golang-builder|1.0.0|jar)
[![Maven 3.0.3+](https://img.shields.io/badge/maven-3.0.3%2b-green.svg)](https://maven.apache.org/)
[![PayPal donation](https://img.shields.io/badge/donation-PayPal-red.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=AHWJHJFBAWGL2)

![mvn-golang](https://raw.githubusercontent.com/raydac/mvn-golang/master/assets/mvngolang.png)

__The Plugin is under development and there is not any ready version yet!__

# Introduction
I very like Maven build tool and use it very actively in my work so that I decided to develop a small maven plug-in to bring possibility to build and GoLang executable applications with the build tool.   
The Plug-in is a full cycle one and allows to build a GoLang application with Maven even if there is not any installed GoLang SDK in OS, in the case the plug-in will download compatible one and unpack an SDK from GoLang page and will be using the SDK in its work.   
Mainly all main commands of GoLang are accessible through the plug-in and their list you can see below:
* build
* clean
* fix
* fmt
* get
* generate
* install
* test
* tool
* vet

# Example
The Part pom.xml below shows how to build 'Hello world' application with the plug-in.
```
  <properties>
    <target.name>helloworld</target.name>
  </properties>

  <profiles>
    <profile> 
      <id>windows</id>
      <activation>
        <os>
          <family>windows</family>
        </os>
      </activation>
      <properties>
        <target.name>helloworld.exe</target.name>
      </properties>
    </profile>
  </profiles>

  <build>
    <plugins>
      <plugin>
        <groupId>com.igormaznitsa</groupId>
        <artifactId>mvn-golang-wrapper</artifactId>
        <version>1.0.0</version>
        <executions>
          <execution>
            <id>golang-build</id>
            <goals>
              <goal>build</goal>
            </goals>
            <configuration>
              <name>${target.name}</name>
            </configuration>
          </execution>
        </executions>
        <configuration>
          <goVersion>1.6</goVersion>
        </configuration>
      </plugin>
    </plugins>
  </build>
```

# Configuration 

About configuration parameters, you can read at [the wiki page](https://github.com/raydac/mvn-golang/wiki/PluginConfigParameters).