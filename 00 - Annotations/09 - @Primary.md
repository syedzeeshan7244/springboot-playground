***What is @Primary in Spring Boot?***

@Primary is used to mark a bean as the default choice when multiple beans of the same type are present in the Spring context.
In other words, if there are two or more beans of the same type, and Spring doesn’t know which one to inject, you can mark one of them with @Primary — that one will be chosen by default.

***When Both @Primary and @Qualifier Are Used***

@Qualifier always takes precedence over @Primary.

That means:

@Primary defines the default bean when no specific bean is requested.

But if you use @Qualifier, Spring will ignore the @Primary bean and inject the bean explicitly named in the @Qualifier.

*** @Qualifier has higher priority when using with @primary annotation ***