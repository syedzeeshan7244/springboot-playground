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

“Start scanning for components (beans) in this package and its sub-packages.”


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