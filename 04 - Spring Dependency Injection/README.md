To really understand Spring, you must grasp Dependency Injection (DI) — it’s the practical implementation of IoC (Inversion of Control).


🌱 *** What is Dependency Injection (DI)? ***

Dependency → An object that another object needs to function.

Injection → Giving (injecting) that dependency from the outside instead of the class creating it itself.

👉 In simple words:
 *** Instead of you creating dependencies manually (new), Spring injects them into your class. ***

*** Spring Container ***

 Primary Function
    Creates and manage objects ( IOC )
    Inject object's dependencies (Dependency Object)

![alt text](<Screenshot 2025-09-30 at 11.59.04 AM.png>)
🔹 Example Without DI

<pre> ``` 

class Engine {}

class Car {
    private Engine engine = new Engine(); // Car creates its own dependency
}
``` <pre> 

❌ Problem: Car is tightly coupled with Engine. If you want Car to use ElectricEngine, you must edit the class.

springboot-playground/04 - Spring Dependency Injection/Screenshot 2025-09-30 at 12.27.29 PM.png 

🔹 Example With DI (Spring Way)

<pre> ``` 
import org.springframework.stereotype.Component;
import org.springframework.beans.factory.annotation.Autowired;

@Component
class Engine {}

@Component
class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) {  // Engine is injected by Spring
        this.engine = engine;
    }

    public void start() {
        System.out.println("Car started with engine: " + engine);
    }
}
``` <pre> 

✅ Now, the Car does not create Engine itself.

Spring’s IoC Container creates Engine and injects it into Car.

Car only “depends” on the existence of an Engine.

🔹 Types of Dependency Injection in Spring

Constructor Injection ✅ (Recommended)
Setter Injection
Field Injection (Not recommended for large apps, but used in quick examples)


*** Constructor Injection ✅ (Recommended) ***
 Use when you have required dependencies.

<pre> ``` 
@Component
class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }
}
``` <pre> 

Setter Injection
use when you have optional dependencies
<pre> ``` 

@Component
class Car {
    private Engine engine;

    @Autowired
    public void setEngine(Engine engine) {
        this.engine = engine;
    }
}
``` <pre> 


<pre> ``` 

@Component
class Car {
    @Autowired
    private Engine engine;
}

``` <pre> 