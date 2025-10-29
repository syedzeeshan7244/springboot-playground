***@Bean Annotation***

@Bean is used inside a @Configuration class to tell Spring “create this object and manage it as a bean.”

It’s similar to defining a <bean> in XML.

@Bean is used inside a @Configuration class to tell Spring “create this object and manage it as a bean.”

It’s similar to defining a <bean> in XML.

@Bean
public DataSource dataSource() {
    return new HikariDataSource();
}

⚙️ ***When to Use @Bean***

Use @Bean when:

You want to define a bean that you can’t annotate directly with @Component, @Service, etc.

You want fine-grained control over bean creation (custom constructor args, initialization methods, etc.).

You’re configuring third-party classes (e.g., a DataSource, ObjectMapper, RestTemplate)

@Configuration
public class RestClientConfig {

    @Bean
    public RestTemplate restTemplate() {
        return new RestTemplate();
    }
}

🧠 Quick Comparison Table

| Annotation       | Applied On | Purpose                                                  | Typical Usage                     |
| ---------------- | ---------- | -------------------------------------------------------- | --------------------------------- |
| `@Configuration` | Class      | Declares a Java class as a source of bean definitions    | Group related beans               |
| `@Bean`          | Method     | Defines a Spring-managed bean from method’s return value | Define beans not easily annotated |


⚡ In Short

@Configuration → “This class defines beans for Spring.”
@Bean → “This method returns a bean that Spring should manage.”
