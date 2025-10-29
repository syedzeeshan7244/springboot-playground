🧩 What Is “JSON Data Binding”?

JSON Data Binding is the process of converting between Java objects and JSON data — automatically.

"Data binding is the process of converting JSON data to a java POJO"

JSON  --> Java POJO

1. Spring uses the Jakson project behind the scenes 
2. By default, Jakson will call appropriate getter/setter method 

Serialization → Java object ➜ JSON

Deserialization → JSON ➜ Java object

This lets your Java app easily send, receive, or store data as JSON — for example, when working with REST APIs.

There Are Two Main Ways in Java

| Approach                 | Library                                        | Description                             |
| ------------------------ | ---------------------------------------------- | --------------------------------------- |
| **Standard Java JSON-B** | `jakarta.json.bind`                            | Official Java API (Jakarta EE standard) |
| **Popular Library**      | **Jackson** (`com.fasterxml.jackson.databind`) | Widely used in Spring Boot              |


Part 2: Jackson (Most Common in Spring Boot)

In Spring Boot, JSON binding is automatically handled by Jackson.

<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.18.0</version> <!-- or latest -->
</dependency>

```Java
import com.fasterxml.jackson.annotation.JsonProperty;

public class Student {
    private int id;
    private String name;

    @JsonProperty("email_address")
    private String email;

    public Student() {}

    public Student(int id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    // Getters and setters...
}

```

Step 3: Serialize and Deserialize using Jackson

```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class JacksonExample {
    public static void main(String[] args) throws Exception {
        ObjectMapper mapper = new ObjectMapper();

        Student student = new Student(1, "Alice", "alice@example.com");

        // Java → JSON
        String json = mapper.writeValueAsString(student);
        System.out.println("Serialized JSON: " + json);

        // JSON → Java
        Student result = mapper.readValue(json, Student.class);
        System.out.println("Deserialized name: " + result.getName());
    }
}

```
🔹 Common Jackson Annotations

| Annotation                          | Purpose                             |
| ----------------------------------- | ----------------------------------- |
| `@JsonProperty("json_name")`        | Rename JSON key                     |
| `@JsonIgnore`                       | Exclude field                       |
| `@JsonFormat(pattern="yyyy-MM-dd")` | Format date/time                    |
| `@JsonCreator` + `@JsonProperty`    | Use constructor for deserialization |
| `@JsonInclude(Include.NON_NULL)`    | Ignore null fields                  |


