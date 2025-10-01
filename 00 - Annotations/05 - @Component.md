🔹 *** What is @Component? ***

- @Component is a Spring stereotype annotation.
- It marks a class as a Spring Bean (an object managed by Spring’s IoC container).
- Once annotated, Spring will auto-detect it during component scanning and create an instance of that class.

![alt text](<Screenshot 2025-09-30 at 12.27.29 PM.png>)

🔹 Example
<pre> ``` 
import org.springframework.stereotype.Component;

@Component
public class Engine {

    public void start() {
        System.out.println("Engine started...");
    }

}
``` <pre> 
 
*** How it Workds ? ***

- When the app starts, Spring scans the package.
- It finds @Component on Engine.
- Spring creates a bean of Engine and stores it in the ApplicationContext.

<pre> ``` 
@Component
public class Car {

    private final Engine engine;

    // Spring injects Engine automatically
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is moving...");
    }
}
``` <pre> 

🔹 Real-Life Analogy

Think of @Component as putting a label/tag on a tool in your workshop:
When you tag a Hammer with @Component, it goes into Spring’s toolbox (ApplicationContext).
Later, when another class (say, Car) needs a Hammer, Spring knows exactly where to fetch it from.