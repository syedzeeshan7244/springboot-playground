🔹 What is Lazy Initialization?

By default, Spring Boot uses Eager Initialization:

When the application starts, Spring creates all beans immediately and keeps them ready in memory.

Lazy Initialization changes this behavior:

Beans are created only when they are first needed (requested by another bean or code).



![alt text](<Screenshot 2025-09-30 at 12.27.29 PM.png>)

🔹 How to Enable Lazy Initialization in Spring Boot
1️⃣ Globally (for all beans)

Add this property in application.properties:

spring.main.lazy-initialization=true


Or in application.yml:

spring:
  main:
    lazy-initialization: true


Now all beans will be initialized lazily.

2️⃣ For a Specific Bean

Use @Lazy on a bean or dependency:

@Component
@Lazy
public class HeavyBean {
    public HeavyBean() {
        System.out.println("HeavyBean created!");
    }
}


This bean will only be created when it’s first used.


🔹 When NOT to use it?

⚠️ If your bean is critical for startup (like database connections, security, message brokers), you don’t want to delay their creation.
⚠️ Lazy beans may cause runtime delays (first use is slower).

🔹 Real-Life Analogy

Eager Initialization → A hotel pre-cooks every possible dish before guests arrive 🍲. Fast service later, but wasteful if no one orders.

Lazy Initialization → The chef only cooks a dish when a guest orders it 🍽️. Startup is fast, but first order takes more time.