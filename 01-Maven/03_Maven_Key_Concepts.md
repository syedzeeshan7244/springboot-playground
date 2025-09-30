* POM files - pom.xml
* Project Coordinates

* Project Object Model File : POM File
    Configuration file for your project
    Basically your "Shopping list" for maven

* POM File Structure    
 ![alt text](<Screenshot 2025-09-29 at 11.53.58 PM.png>)


Project meta data   
    Project name, version etc, output file type: JAR,WAR
Dependencies
    List of project we depend on spring, hibernate, etc
plug-ins 

![alt text](<Screenshot 2025-09-29 at 11.56.26 PM.png>)

Project Coordinates

![alt text](<Screenshot 2025-09-29 at 11.57.29 PM.png>)



🔑 Key Concepts in Maven
1. POM (Project Object Model)

The heart of every Maven project: pom.xml.

Defines project info, dependencies, plugins, and build configurations.

Example:

<pre> ```
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>3.2.5</version>
        </dependency>
    </dependencies>
</project>

</pre>```

2. Dependencies

External libraries your project needs.

Declared inside pom.xml.

Maven downloads them from repositories automatically.

3. Repositories

Storage locations for dependencies and plugins.

Types:

Local Repository → on your computer (~/.m2/repository).

Central Repository → Maven Central (public, huge library).

Remote Repository → custom/private repos (e.g., Nexus, Artifactory).

4. Coordinates (GAV – Group, Artifact, Version)

How Maven uniquely identifies artifacts.

GroupId → org, company, or project name (e.g., org.springframework.boot).

ArtifactId → name of the project/module (e.g., spring-boot-starter-web).

Version → specific release (e.g., 3.2.5).

Together: org.springframework.boot:spring-boot-starter-web:3.2.5

5. Build Lifecycle

A sequence of steps (phases) Maven goes through to build a project.

Main lifecycles:

default → build, test, package, install, deploy.

clean → removes old build files.

site → generates documentation.

6. Phases

Stages in the build lifecycle. Examples:

validate → check project structure.

compile → compile source code.

test → run unit tests.

package → package compiled code into JAR/WAR.

install → install into local repo.

deploy → deploy to remote repo.

7. Plugins & Goals

Plugins extend Maven’s functionality.

Each plugin has goals (tasks).

Example: maven-compiler-plugin has a compile goal.

You run them via commands like:

mvn clean install
mvn spring-boot:run

8. Archetypes

Project templates provided by Maven.

Example:

mvn archetype:generate


lets you quickly create a new project with a predefined structure.

9. Multi-Module Projects

A parent POM can manage multiple child projects (modules).

Useful in microservices or large applications.

🚀 In Short:

POM → defines the project.

Dependencies → libraries your app needs.

Repositories → where dependencies come from.

GAV Coordinates → unique artifact identity.

Lifecycle/Phases → steps in building your project.

Plugins/Goals → extra functionality.

Archetypes → project templates.

Modules → manage large projects.

