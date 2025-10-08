The @RestController annotation in Spring Boot / Spring MVC is a specialized version of @Controller that is used to build RESTful web services.

🔹 ***What it does***
Marks a class as a controller where every method returns a REST API response instead of rendering a view (like JSP, Thymeleaf, etc.).

It’s basically @Controller + @ResponseBody combined.

@Controller tells Spring that the class handles web requests.

@ResponseBody tells Spring that the return value of methods should be written directly to the HTTP response body (usually JSON or XML).

```java 
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring Boot!";
    }
}
```
📌 ***What happens here:***

When you hit http://localhost:8080/hello, you get plain text response:

Hello, Spring Boot!

Without @RestController, you’d have to manually add @ResponseBody to each method.

🔹 ***When to use***
Use @RestController when you are building a REST API (JSON/XML responses).
Use plain @Controller if you want to return views (HTML pages).

***FAQ***

🌟 ***What is @RestController? / What does @RestController do ?***

@RestController is a Spring annotation used to create RESTful web services.
It tells Spring that the class:
Is a controller (just like @Controller), and

Every method inside will return data directly as a response body (usually JSON) instead of rendering a view (like JSP or HTML).

***In short:***
@RestController makes your class a REST API endpoint provider — Spring automatically converts method return values into HTTP responses (usually JSON). 

Added.