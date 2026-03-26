# Dependency Injection in Spring Framework

## What is Dependency Injection?

**Dependency Injection (DI)** is a design pattern used in the Spring Framework where the framework provides (injects) required dependencies into a class, instead of the class creating them itself.

---

##  Why is Dependency Injection Important?

Dependency Injection helps in:

* **Reducing tight coupling** between classes
* **Making code easier to test** (supports mocking dependencies)
* **Improving maintainability and flexibility**
*  **Following the Inversion of Control (IoC) principle**
* **Promoting cleaner and modular design**

---

##  Example: Constructor-Based Dependency Injection

###  Project Structure

```
src/main/java/com/example/demo/
│
├── DemoApplication.java
├── Engine.java
└── Car.java
```

---

### Engine Class

```java
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class Engine {

    public void start() {
        System.out.println("Engine started");
    }
}
```

---

###  Car Class

```java
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class Car {

    private final Engine engine;

    // Constructor Injection
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is moving");
    }
}
```

---

### Main Application Class

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(DemoApplication.class, args);

        Car car = context.getBean(Car.class);
        car.drive();
    }
}
```

---

## Explanation of the Example

* `Engine` is a dependency of `Car`
* Both classes are annotated with `@Component`, so Spring manages them as beans
* Spring automatically injects the `Engine` object into `Car` using **constructor injection**
* The `Car` class does not create the `Engine` object using `new` → this achieves **loose coupling**

---

## Important Notes

* From Spring 4.3 onwards, `@Autowired` is **optional** for a single constructor
* Constructor injection is the **recommended approach**
* Spring manages object creation using the **IoC container**

---

##  Summary

> Dependency Injection allows Spring to manage and inject dependencies, making applications loosely coupled, easier to test, and more maintainable.
