The @PostConstruct annotation in Spring Boot (and more generally in Java using Jakarta / Java EE) is used to mark a method that should be executed once immediately after the bean’s initialization — that is, after dependency injection is complete, but before the bean is used.

🔍 Purpose

When you annotate a method with @PostConstruct, Spring will automatically call that method after:

The bean is created,
All dependencies are injected (via @Autowired, constructor, etc.),
And any configuration properties are set.
This is a convenient way to perform initialization logic, such as:
Setting up resources,
Performing validation,
Preloading data,
Logging startup messages, etc.

import jakarta.annotation.PostConstruct;
import org.springframework.stereotype.Component;

@Component
public class DataInitializer {

    @PostConstruct
    public void init() {
        System.out.println("DataInitializer bean created. Running post-construction logic...");
        // e.g., preload data or perform configuration setup
    }
}

When the Spring container creates the DataInitializer bean, it automatically calls init() after all dependencies have been injected.

⚙️ Lifecycle Order

For a typical Spring-managed bean, the lifecycle goes like this:
Bean is instantiated.
Dependencies are injected (@Autowired).
@PostConstruct methods are called.
Bean is ready for use.
When the context is shutting down, @PreDestroy (if defined) is called.
