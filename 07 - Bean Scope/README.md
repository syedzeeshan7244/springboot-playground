🔹 ***What is a Bean Scope?***

In Spring, a bean scope defines how and when a bean is created, shared, and managed by the Spring container.

Think of it like:

    “How long does a bean live, and who can use it?”

🧱 ***Common Bean Scopes in Spring Boot***

Spring provides several scopes, but the most common ones are:

| Scope                     | Description                              | Created            | Shared                      |
| ------------------------- | ---------------------------------------- | ------------------ | --------------------------- |
| **singleton** *(default)* | One instance per Spring container        | Once               | Shared across the whole app |
| **prototype**             | New instance every time it’s requested   | On every injection | Not shared                  |
| **request**               | One instance per HTTP request (Web only) | Per HTTP request   | No                          |
| **session**               | One instance per HTTP session (Web only) | Per session        | No                          |
| **application**           | One instance per ServletContext          | Once per web app   | Shared                      |
| **websocket**             | One instance per WebSocket session       | Per WebSocket      | No                          |


1️⃣ ***Singleton (Default)***

Default scope in Spring Boot, Spring Container creates only once instance of the bean. It is cached in memory.

Every time you @Autowired MyService, you get the same instance.

✅ Good for stateless beans like services, repositories, etc.
⚠️ Not good for storing request-specific data.

![alt text](<Screenshot 2025-10-02 at 1.24.01 AM.png>)

Only one instance of the bean per Spring container.

All @Autowired injections of this bean point to the same object.

@Component
public class Engine { }

✅ This is the default scope.

2️⃣ ***Prototype***


![alt text](<Screenshot 2025-10-02 at 1.24.43 AM.png>)


Creates a new bean instance every time you request it.

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

@Component
@Scope("prototype")
public class MyPrototypeBean {
    public MyPrototypeBean() {
        System.out.println("Prototype bean created");
    }
}

Every time you inject or get it from the context, a new object is created.


3️⃣ ***Request Scope (Web Applications)***

Creates a new bean for each HTTP request.

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;
import org.springframework.web.context.WebApplicationContext;

@Component
@Scope(WebApplicationContext.SCOPE_REQUEST)
public class MyRequestBean {
    // Unique per HTTP request
}

✅ Perfect for beans that hold request-specific data (e.g., request headers, metadata).
⚠️ Works only in a web-aware Spring Boot app.


4️⃣ ***Session (Web apps only 🌐)***

One bean instance per user session.

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;
import org.springframework.web.context.WebApplicationContext;

@Component
@Scope(WebApplicationContext.SCOPE_SESSION)
public class MySessionBean {
    // Unique per HTTP session
}

✅ Great for user session data (e.g., shopping cart, user preferences).
⚠️ Exists only for web apps with HTTP sessions.


5️⃣ ***Application (Web apps only 🌐)***

One bean instance per ServletContext (shared across the whole web application).

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;
import org.springframework.web.context.WebApplicationContext;

@Component
@Scope(WebApplicationContext.SCOPE_APPLICATION)
public class MyApplicationBean {
    // Shared for all users
}

If Engine is singleton → both Car beans get the same engine instance.

If Engine is prototype → each Car gets a different engine instance.

🔹 ***Real-Life Analogy***

Singleton → A single water tank in a building (all flats share it).

Prototype → Each flat has its own water tank.

Request → Each guest at a restaurant gets their own plate.

Session → Each customer has their own table for the whole meal.

Application → The restaurant menu is the same for everyone.

🧠***Summary Table***

| Scope           | Lifecycle            | Usage                          |
| --------------- | -------------------- | ------------------------------ |
| **singleton**   | One per container    | Default, stateless services    |
| **prototype**   | New for each request | Temporary/stateful beans       |
| **request**     | Per HTTP request     | Request-specific data          |
| **session**     | Per user session     | Session data (e.g., user info) |
| **application** | Per ServletContext   | Shared app-level objects       |


✅ In short:
Bean Scope defines how Spring creates and shares beans inside the container. Singleton (default) = one instance, Prototype = new instance each time, others (request, session, application, websocket)