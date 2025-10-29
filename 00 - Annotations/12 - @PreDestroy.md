The @PreDestroy annotation in Spring Boot (and in the Jakarta / Java EE specification) is used to mark a method that should be called just before a Spring bean is destroyed — for example, when the application context is shutting down.

It’s the counterpart to @PostConstruct.
Where @PostConstruct handles initialization, @PreDestroy handles cleanup.

🔍 Purpose

@PreDestroy is used for defining cleanup logic that needs to run before a bean is removed from the Spring container, such as:

Closing resources (files, sockets, database connections, etc.)

Stopping background threads

Releasing locks

Flushing caches

Logging shutdown events


import jakarta.annotation.PreDestroy;
import jakarta.annotation.PostConstruct;
import org.springframework.stereotype.Component;

@Component
public class ConnectionManager {

    @PostConstruct
    public void init() {
        System.out.println("ConnectionManager initialized: Opening connection...");
        // e.g., open a database connection
    }

    @PreDestroy
    public void cleanup() {
        System.out.println("ConnectionManager being destroyed: Closing connection...");
        // e.g., close the connection
    }
}


🌀 What happens:

When the Spring container creates this bean, it calls init() after dependency injection.

When the application context is shutting down (for example, on application exit), Spring automatically calls cleanup() before destroying the bean.


⚙️ Lifecycle Order Summary

Here’s the typical lifecycle of a Spring bean:

Bean is instantiated.
Dependencies are injected (@Autowired or constructor).
@PostConstruct method(s) run.
Bean is used by the application.
Spring context shuts down.
@PreDestroy method(s) run for cleanup.
Bean is destroyed and garbage collected.

