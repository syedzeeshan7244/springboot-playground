🔹 What is Component Scanning?

Component scanning is how Spring automatically finds and registers your beans (@Component, @Service, @Repository, @Controller, etc.) into the ApplicationContext.


Instead of creating beans manually in XML or Java config, Spring scans your packages and picks them up.

🔹 How it works in Spring Boot

In your main class, you usually have:

@SpringBootApplication
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}


@SpringBootApplication is a shortcut for:

@Configuration

@EnableAutoConfiguration

@ComponentScan


@ComponentScan is the key — it tells Spring:

“Start scanning for components (beans) in this package and its sub-packages. otherwise it won't scan the subpackages.”


👉 Example: If your main class is in com.example.app, then Spring will scan:

com.example.app
com.example.app.controller
com.example.app.service
com.example.app.repository

🔹 Example
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class Engine {
    public void start() {
        System.out.println("Engine started...");
    }
}

package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class Car {
    private final Engine engine;

    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is moving...");
    }
}


✅ You don’t need to configure Engine or Car anywhere.
Spring finds them via component scanning and injects automatically.



🔹 Customizing Component Scan

You can override default scanning:

@SpringBootApplication
@ComponentScan(basePackages = {"com.example.demo", "com.example.utils"})
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}


Here Spring will scan both com.example.demo and com.example.utils

🔹 Real-Life Analogy

Think of Spring’s component scanning like a security scanner at an airport:

The scanner looks at everyone (classes) passing through.

If someone has the right tag (@Component, @Service, etc.), they are allowed inside (registered as a bean).


✅ In short:
Component Scanning = Spring Boot automatically discovers and registers beans from the package where the main class resides and its sub-packages.



What is Component Scanning?

Component scanning is how Spring automatically detects and registers beans (classes) in the application context — without you needing to explicitly define them in a configuration file.

It looks for classes annotated with:

@Component

@Service

@Repository

@Controller

@RestController

@Configuration

and then automatically creates objects (beans) for them in the Spring container.

🧭 How Scanning Works

When you use:

@SpringBootApplication
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}


The annotation @ComponentScan (included inside @SpringBootApplication) tells Spring to scan the package of this class and all its sub-packages.

For example:

com.example.myapp
 ┣ src/main/java
 ┃ ┣ com/example/myapp/MyApp.java
 ┃ ┣ com/example/myapp/controller/UserController.java
 ┃ ┣ com/example/myapp/service/UserService.java
 ┃ ┗ com/example/myapp/repository/UserRepository.java


Since MyApp is in the com.example.myapp package, Spring will automatically detect all components in:

com.example.myapp.controller

com.example.myapp.service

com.example.myapp.repository

✅ Everything gets discovered because they are sub-packages of the root package.

⚠️ What Happens If You Place Classes Outside the Package?

Example:

com.example.myapp
 ┣ MyApp.java
 ┗ controller/
     ┗ UserController.java
anotherpackage/
 ┗ SomeService.java


If SomeService.java is in anotherpackage (not under com.example.myapp), Spring will not scan it automatically — and you’ll get an error like:

No qualifying bean of type 'com.example.anotherpackage.SomeService' available


because Spring never created a bean for it.

🧠 How to Fix It (if you need external packages)

You can explicitly tell Spring which packages to scan:

@SpringBootApplication(scanBasePackages = {"com.example.myapp", "com.example.anotherpackage"})
public class MyApp { ... }


or separately:

@ComponentScan(basePackages = {"com.example.myapp", "com.example.anotherpackage"})


This ensures Spring includes those packages in its scanning.

✅ Best Practice

Keep your main class at the top of your package hierarchy, for example:

com.example.projectname
 ┣ ProjectNameApplication.java  ← main class here
 ┣ controller/
 ┣ service/
 ┣ repository/
 ┗ model/


This way, Spring Boot automatically scans everything without any manual configuration.

