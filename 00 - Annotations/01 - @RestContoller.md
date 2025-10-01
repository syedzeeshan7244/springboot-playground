The @RestController annotation in Spring Boot / Spring MVC is a specialized version of @Controller that is used to build RESTful web services.

🔹 What it does

Marks a class as a controller where every method returns a REST API response instead of rendering a view (like JSP, Thymeleaf, etc.).

It’s basically @Controller + @ResponseBody combined.

@Controller tells Spring that the class handles web requests.

@ResponseBody tells Spring that the return value of methods should be written directly to the HTTP response body (usually JSON or XML).

<pre> ```java 
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring Boot!";
    }
}
``` </pre>

📌 What happens here:

When you hit http://localhost:8080/hello, you get plain text response:

Hello, Spring Boot!

Without @RestController, you’d have to manually add @ResponseBody to each method.

🔹 When to use

Use @RestController when you are building a REST API (JSON/XML responses).

Use plain @Controller if you want to return views (HTML pages).