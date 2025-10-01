🔹 *** What is @Autowired? ***

- @Autowired is used in Spring for Dependency Injection (DI).
- It tells Spring: “Hey, please give me the object (bean) I need here.”
- Spring will look inside its IoC Container (ApplicationContext) and inject the matching bean automatically.

🔹 Where can we use it?

- Constructor
- Setter method
- Field (directly on variable)

🔹 ***What happens behind the scenes?***

- Spring starts the app.
- Spring scans for beans (classes with @Component, @Service, @Repository, etc.).
- When it sees @Autowired, it checks if a matching bean is available.
  - If one bean matches → it injects it.
  - If multiple beans match → you may need @Qualifier to tell Spring which one.
  - If no bean found → error (unless you make it optional with @Autowired(required = false)).

🔹 Quick Analogy

Think of @Autowired like saying:
"Spring, please plug in the right charger (dependency) into my phone (class). I don’t want to find or build the charger myself." ⚡📱