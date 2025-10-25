🌱 *** What is IoC (Inversion of Control)? ***

Normally, in traditional Java programming, your classes create and control their own dependencies using new.

With IoC, this control is inverted: instead of your code creating objects, ***the Spring IoC Container creates and manages them***, then injects them where needed.

👉 In simple words:

“***You don’t create objects manually; Spring creates and provides them to you.***”

"*** The approach of outsourcing the construction and management of objects ***"

***Spring Container Primary function**

1. Create and manage objects (IOC)
2. Inject object dependencies (Dependency injection)


![alt text](<Screenshot 2025-09-30 at 12.58.24 AM.png>)

🔹 Example Without IoC

<pre> ``` 

class Engine {}

class Car {
    private Engine engine = new Engine(); // Car creates its own Engine
}
``` <pre> 

❌ Here, Car is tightly coupled to Engine. Hard to test and replace with a different engine.

🔹 Example With IoC (Dependency Injection) 
<pre> ``` 

import org.springframework.stereotype.Component;
import org.springframework.beans.factory.annotation.Autowired;

@Component
class Engine {}

@Component
class Car {
    
    private Engine engine;

    @Autowired
    public Car(Engine engine) {   // Spring injects Engine
        this.engine = engine;
    }

}
``` <pre> 

✅ Now, Spring’s IoC container creates the Engine object and injects it into Car.

Car doesn’t care how Engine is created.

Easy to replace Engine with another type (like ElectricEngine) without modifying Car.

🔹 How IoC works in Spring

Spring uses an IoC Container ( like ApplicationContext or BeanFactory ).

The container:

Reads configuration (@Configuration, @Component, @Bean, or XML).

Creates objects (beans).

Injects dependencies where required (@Autowired, @Value, etc.).

Manages the lifecycle of beans (singleton, prototype, etc.).

👉 In short:IoC = Giving control of object creation and dependency management to the Spring Container instead of doing it manually in your code.

🚀 Benefits of IoC

* Loose coupling → classes depend on abstractions, not implementations.
* Easier testing → you can inject mock objects.
* Better maintainability → easy to replace or upgrade components.
* Centralized configuration → dependencies managed in one place.
