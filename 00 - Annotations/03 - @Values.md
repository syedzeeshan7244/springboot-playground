The @Value annotation in Spring Framework / Spring Boot is used to inject values into fields, method parameters, or constructor arguments directly from:

Properties files (application.properties or application.yml)

Environment variables / system properties

Default values

SpEL (Spring Expression Language) expressions

🔹 Example 1: Injecting from application.properties

Suppose you have this in application.properties:

app.name=My Spring App
app.version=1.0.0


You can inject these into a class:

import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component
public class AppConfig {

    @Value("${app.name}")
    private String appName;

    @Value("${app.version}")
    private String version;

    public void printConfig() {
        System.out.println("App Name: " + appName);
        System.out.println("Version: " + version);
    }
}


Output:

App Name: My Spring App
Version: 1.0.0


🔹 Example 4: SpEL (Spring Expression Language)
@Value("#{2 * 10}")
private int number;  // number = 20

@Value("#{systemProperties['user.name']}")
private String userName;  // current OS username



🚀 In Short:

@Value = inject values into fields from properties, env vars, or expressions.

Super useful for making apps configurable without changing code.
