***@Configuration Annotation***

@Configuration marks a class as a source of Spring bean definitions — basically, a configuration class that tells Spring how to create and wire beans.

It replaces old-style applicationContext.xml configuration files.

import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {
    // defines beans here
}


⚙️ ***Purpose***

When Spring Boot starts:
It looks for classes annotated with @Configuration.
It treats them like containers for @Bean methods.
Each @Bean method inside produces and registers a Spring bean in the application context.

| Annotation       | Applied On | Purpose                                                  | Typical Usage                     |
| ---------------- | ---------- | -------------------------------------------------------- | --------------------------------- |
| `@Configuration` | Class      | Declares a Java class as a source of bean definitions    | Group related beans               |
| `@Bean`          | Method     | Defines a Spring-managed bean from method’s return value | Define beans not easily annotated |


⚡ In Short

@Configuration → “This class defines beans for Spring.”
@Bean → “This method returns a bean that Spring should manage.”


