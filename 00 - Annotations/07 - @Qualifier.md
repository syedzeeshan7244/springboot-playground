🔹 The Problem

Spring uses @Autowired to inject dependencies.

But if there are multiple beans of the same type, Spring doesn’t know which one to inject → it throws an error:

🔹 The Solution → @Qualifier

@Qualifier helps you tell Spring which exact bean to inject when there are multiple candidates.

🔹 Example
Without @Qualifier → Ambiguity
@Component
class PetrolEngine implements Engine {}

@Component
class DieselEngine implements Engine {}

@Component
class Car {
    private final Engine engine;

    @Autowired   // ❌ ERROR: Two beans of type Engine
    public Car(Engine engine) {
        this.engine = engine;
    }
}


Spring doesn’t know whether to use PetrolEngine or DieselEngine.



With @Qualifier → Clear choice
@Component
class PetrolEngine implements Engine {}

@Component
class DieselEngine implements Engine {}

@Component
class Car {
    private final Engine engine;

    @Autowired
    public Car(@Qualifier("dieselEngine") Engine engine) {  // ✅ explicitly choose
        this.engine = engine;
    }
}


✔ Now Spring injects the DieselEngine bean.
 
