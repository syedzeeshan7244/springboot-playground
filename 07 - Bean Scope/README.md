🔹 ***What is a Bean Scope?***

A scope in Spring defines how long a bean lives and how many instances of it exist in the Spring container.
By default, Spring Boot uses singleton scope (only one instance of each bean).


🔹 ***Common Bean Scopes in Spring Boot

1️⃣ Singleton (Default)

![alt text](<Screenshot 2025-10-02 at 1.24.01 AM.png>)

Only one instance of the bean per Spring container.

All @Autowired injections of this bean point to the same object.

@Component
public class Engine { }

✅ This is the default scope.

2️⃣ Prototype

![alt text](<Screenshot 2025-10-02 at 1.24.43 AM.png>)

A new instance is created every time the bean is requested.

@Component
@Scope("prototype")
public class Engine { }


⚠️ Spring does not manage the full lifecycle of prototype beans (no @PreDestroy).

3️⃣ Request (Web apps only 🌐)

One bean instance per HTTP request.

Commonly used in Spring MVC apps.

@Component
@Scope("request")
public class RequestBean { }

4️⃣ Session (Web apps only 🌐)

One bean instance per HTTP session.

Used when you want to store data across multiple requests in the same session.

@Component
@Scope("session")
public class SessionBean { }

5️⃣ Application (Web apps only 🌐)

One bean instance per ServletContext (shared across the whole application).

@Component
@Scope("application")
public class ApplicationBean { }

6️⃣ WebSocket (if using STOMP/WebSocket messaging)

One bean instance per WebSocket session.

@Component
@Scope("websocket")
public class WebSocketBean { }

🔹 Example Demonstration
@Component
@Scope("singleton")  // try changing to prototype
public class Engine {
    public Engine() {
        System.out.println("Engine created: " + this);
    }
}

@Component
public class Car {
    @Autowired
    private Engine engine;

    public void start() {
        System.out.println("Car with engine: " + engine);
    }
}


If Engine is singleton → both Car beans get the same engine instance.

If Engine is prototype → each Car gets a different engine instance.

🔹 Real-Life Analogy

Singleton → A single water tank in a building (all flats share it).

Prototype → Each flat has its own water tank.

Request → Each guest at a restaurant gets their own plate.

Session → Each customer has their own table for the whole meal.

Application → The restaurant menu is the same for everyone.

✅ In short:
Bean Scope defines how Spring creates and shares beans inside the container. Singleton (default) = one instance, Prototype = new instance each time, others (request, session, application, websocket)