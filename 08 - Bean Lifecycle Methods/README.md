🌱 ***Spring Bean Lifecycle***

A Spring bean goes through several stages from ***creation → initialization → destruction.***
Spring manages all of this inside the ApplicationContext (IoC Container).

![alt text](<Screenshot 2025-10-02 at 1.35.46 PM.png>)

You can add custom code during bean initializatio.
    1. calling customer buiness logic methods
    2. setting up handles to resources (db,sockets,file etc)
You can add customer code during bean destruction
    1. calling customer business logic method
    2. clean up handles to resources (db, sockets, file etc)    

![alt text](<Screenshot 2025-10-02 at 1.41.31 PM.png>)

🔹 ***Steps in Bean Lifecycle***

1. Instantiation

Spring creates the bean instance (using new).

2. Populate Properties (Dependency Injection)

Spring injects dependencies into the bean (via @Autowired, @Value, constructor/setters, etc.).

3. BeanNameAware & BeanFactoryAware Callbacks (Optional)

If the bean implements these interfaces, Spring provides metadata like bean name or factory reference.

4. BeanPostProcessor (before initialization)

Any custom logic defined in a BeanPostProcessor is run before bean initialization.

5. Initialization

If the bean implements InitializingBean, Spring calls afterPropertiesSet().

If a bean has a custom init method (configured with @Bean(initMethod=...) or @PostConstruct), it is called here.

6. BeanPostProcessor (after initialization)

Post-processing logic runs after initialization.

7. Bean is Ready for Use 🚀

8. Destruction (when container shuts down)

If the bean implements DisposableBean, Spring calls destroy().

If a custom destroy method is specified (@Bean(destroyMethod=...) or @PreDestroy), it is called.

Ways to Hook into Lifecycle

1. Using @PostConstruct and @PreDestroy

@Component
public class MyBean {

    @PostConstruct
    public void init() {
        System.out.println("Bean is initialized ✅");
    }

    @PreDestroy
    public void cleanup() {
        System.out.println("Bean is about to be destroyed ❌");
    }
}

🔹 ***Lifecycle Summary in Order***

1. Constructor → Bean created

2. Dependency Injection → Dependencies injected

3. @PostConstruct / afterPropertiesSet() / initMethod → Initialization logic

4. Bean is ready → Used in application

5. @PreDestroy / destroy() / destroyMethod → Cleanup