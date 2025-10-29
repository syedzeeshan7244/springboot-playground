In Spring Boot (and more generally, in Java Persistence API – JPA), the @Entity annotation is used to mark a Java class as a JPA entity, meaning that it represents a table in a relational database.

🧩 Definition

import jakarta.persistence.Entity;

@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String username;
    private String email;
}

📘 ***What It Does***

When you annotate a class with @Entity, you are telling JPA (via Hibernate or another ORM provider):
This class should be mapped to a database table.
Each instance of this class represents a row in that table.
The class’s fields correspond to columns in the table.

⚙️ ***Common Related Annotations***

| Annotation                    | Purpose                                                                |
| ----------------------------- | ---------------------------------------------------------------------- |
| `@Table(name = "users")`      | Customizes the table name (default is class name).                     |
| `@Id`                         | Marks the primary key field.                                           |
| `@GeneratedValue`             | Defines how the primary key value is generated (e.g., auto-increment). |
| `@Column(name = "user_name")` | Customizes the column name.                                            |
| `@Transient`                  | Excludes a field from persistence.                                     |


