# npm-mvn-nexus load zip dependency

## How to load and unzip a dependency from nexus3 ?

 - follow the guidelines from this repository to deploy your zipped web application
 
https://github.com/louisamoros/npm-mvn-nexus

 - set mirrors in maven settings
 
`vi ~/.m2/settings.xml`

```xml
<!-- add those lines to mirrors section -->
<mirror>
    <id>nexus</id>
	<name>Nexus local</name>
	<url>http://localhost:8081/repository/maven-public/</url>
	<mirrorOf>nexus</mirrorOf>
</mirror>
```
```xml
<!-- add those lines to repositories section -->
<repository>
    <id>nexus</id>
	<url>http://localhost:8081/repository/maven-public/</url>
	<releases>
	    <enabled>true</enabled>
    </releases>
    <snapshots>
	    <enabled>true</enabled>
	</snapshots>
</repository>
```

 - load and unzip dependency into project
 
`mvn clean package && ls -la target/dependency`