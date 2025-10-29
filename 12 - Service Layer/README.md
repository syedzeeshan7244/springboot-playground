💡 Purpose of the Service Layer

The Service Layer sits between the Controller (web/API layer) and the Repository (data access layer).
Its main purpose is to handle business logic — the actual “rules” or “operations” your application performs.

⚙️ Key Responsibilities

Encapsulate Business Logic
It contains the core logic of your application — the “what should happen” part.
Example: Calculating salaries, validating data, applying discounts, checking business rules, etc.

```java

public double calculateBonus(Employee employee) {
    if (employee.getYearsOfService() > 5) {
        return employee.getSalary() * 0.10;
    }
    return employee.getSalary() * 0.05;
}

```

Coordinate Between Layers

The service layer calls the repository (DAO) to get or save data.

The controller calls the service, not the repository directly.

This separation keeps your controller “thin” and your business logic centralized.

```java

@Service
public class EmployeeService {
    @Autowired
    private EmployeeRepository employeeRepository;

    public List<Employee> findAllEmployees() {
        return employeeRepository.findAll();
    }
}

```

Transaction Management

In Spring, you often mark service methods with @Transactional so that database operations inside them happen in a single transaction.

Reusability

Services can be reused by multiple controllers, schedulers, or other components.

Simplified Testing

You can test your service logic independently of the web layer (controllers).

com.example.employee
│
├── controller
│   └── EmployeeController.java
├── service
│   └── EmployeeService.java
├── repository
│   └── EmployeeRepository.java
└── entity
    └── Employee.java

Controller → handles HTTP requests and responses.

Service → contains business logic.

Repository → interacts with the database.

| Layer      | Responsibility                   |
| ---------- | -------------------------------- |
| Controller | Handle HTTP requests & responses |
| Service    | Handle business logic            |
| Repository | Handle database operations       |


@Component is the core stereotype annotation in Spring — it marks a class as a Spring Bean so that it can be automatically detected during component scanning and registered in the Spring ApplicationContext.

Other annotations like @Service, @Repository, and @Controller are specialized forms of @Component.


                         +-------------------+
                         |  @Component       |
                         |  (Generic Bean)   |
                         +---------+---------+
                                   |
         --------------------------------------------------
         |                        |                      |
 +----------------+     +----------------+     +----------------+
 |  @Service      |     |  @Repository   |     |  @Controller   |
 | (Business Logic)|    | (Data Access)  |     | (Web Layer)    |
 +----------------+     +----------------+     +----------------+


