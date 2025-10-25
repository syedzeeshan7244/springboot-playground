🔹 ***What is @Scope?***

By default, Spring beans are singleton → only one instance of the bean is created and shared.

@Scope lets you change this behavior by specifying a different bean scope.


🔹 Usage
@Component
@Scope("prototype")
public class Engine {
    public Engine() {
        System.out.println("Engine created: " + this);
    }
}


Here, every time Spring injects Engine, it will create a new instance instead of reusing the same one.

🔹 ***Available Scopes in Spring Boot***

***singleton (default)***

One instance per Spring container.

@Scope("singleton")


***prototype***

A new bean instance is created every time it’s requested.

@Scope("prototype")


request (Web apps only 🌐)

One bean per HTTP request.

@Scope("request")


session (Web apps only 🌐)

One bean per HTTP session.

@Scope("session")


application (Web apps only 🌐)

One bean per ServletContext (entire application).

@Scope("application")


websocket (WebSocket apps only)

One bean per WebSocket session.

@Scope("websocket")


