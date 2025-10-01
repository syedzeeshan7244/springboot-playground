The @GetMapping annotation in Spring Boot / Spring MVC is used to handle HTTP GET requests for a specific URL.

🔹 ***What it does***
Maps a GET request (like when you open a link in a browser) to a controller method.
It’s a shortcut for @RequestMapping(method = RequestMethod.GET).

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

```<pre> 


🔹 Key points about @GetMapping

Handles only GET requests.

Example: Clicking a link or typing a URL in a browser.

Supports path variables and query parameters.

<pre> ```
@GetMapping("/hello/{name}")
public String greet(@PathVariable String name) {
    return "Hello, " + name + "!";
}


URL: /hello/zeeshan → Response: Hello, zeeshan!

@GetMapping("/hello")
public String greetWithQuery(@RequestParam String name) {
    return "Hello, " + name + "!";
}
```<pre> 

URL: /hello?name=Zeeshan → Response: Hello, Zeeshan!

👉 In short:
@GetMapping is used to map HTTP GET requests to a specific method in your controller.