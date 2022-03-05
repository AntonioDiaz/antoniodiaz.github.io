# Maven review

## Links
https://www.baeldung.com/maven  
https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html  
https://jetbrains.com/idea/guide/tutorials/working-with-maven/introduction/  
https://cguntur.me/2020/05/20/understanding-apache-maven-the-series/


## Concepts
* Project Identifiers - (GAV):
    * `groupId`
    * `artifactId`
    * `version`
    * `packaging`: war/jar/zip
* Dependecies: exterenal libraries
* Repositories
    * Default local repository: `.md/repository`
    * Default central repository: https://search.maven.org/
* Properties
```xml
<properties>
    <spring.version>4.3.5.RELEASE</spring.version>
</properties>
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-core</artifactId>
        <version>${spring.version}</version>
    </dependency>
</dependencies>
```
* __Build__: default maven goal.  
Default maven seccion:
```xml
<build>
    <defaultGoal>install</defaultGoal>
    <directory>${basedir}/target</directory>
    <finalName>${artifactId}-${version}</finalName>
    <filters>
      <filter>filters/filter1.properties</filter>
    </filters>
    //...
</build>
```
* __Profiles__: set of configuration values
* __Plugin__
* __Goal__
    * `mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false`
* __Lifecycle__: an ordered sequence of phase
* __Phase__: is a step in the build lifecycle  

### Default lifecycle phases 
|  |  |
|---|---|
| validate | checks the correctness of the project |
| compile | compiles the provided source code into binary artifacts |
| test | executes unit tests |
| package | packages compiled code into an archive file |
| integration-test | executes additional tests, which require the packaging |
| verify | checks if the package is valid |
| install | installs the package file into the local Maven repository |
| deploy | deploys the package file to a remote server or repository |

### Two other Maven lifecycles
|  |  |
|---|---|
| clean | cleans up artifacts created by prior builds |
| site | generates site documentation for this project |
