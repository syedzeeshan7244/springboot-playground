In Spring Boot, the ***@ControllerAdvice annotation** is used to define global logic that applies to multiple controllers — most commonly for exception handling and data binding.

Think of it like a “global controller helper” that sits across all your controllers.

```java 
import org.springframework.web.bind.annotation.ControllerAdvice;

@ControllerAdvice
public class GlobalExceptionHandler {
    // Global exception handling logic here
}
```
🎯 Purpose of @ControllerAdvice

It allows you to:
Handle exceptions globally — instead of repeating try-catch in every controller.
Bind common data to all controllers (e.g., adding attributes to the model).
Apply @InitBinder logic (custom form validations, formatters, etc.) globally.


| Concept          | Explanation                                                       |
| ---------------- | ----------------------------------------------------------------- |
| **Annotation**   | `@ControllerAdvice`                                               |
| **Package**      | `org.springframework.web.bind.annotation`                         |
| **Purpose**      | Apply global logic (mainly exception handling) to all controllers |
| **Common Pair**  | `@ExceptionHandler`, `@ModelAttribute`, `@InitBinder`             |
| **REST Version** | `@RestControllerAdvice`                                           |



🚀 In short:
@ControllerAdvice lets you write one centralized place for handling exceptions, adding model data, or configuring data binding across all your Spring Boot controllers — keeping your code cleaner and easier to maintain.
