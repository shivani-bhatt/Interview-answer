# Dependency Injection in Spring Framework

##  What is Dependency Injection?

**Dependency Injection (DI)** is a design pattern used in the Spring Framework where the framework provides (injects) required dependencies into a class, instead of the class creating them itself.

---

##  Why is Dependency Injection Important?

Dependency Injection helps in:

* **Reducing tight coupling** between classes
*  **Making code easier to test** (supports mocking dependencies)
*  **Improving maintainability and flexibility**
*  **Following the Inversion of Control (IoC) principle**
*  **Promoting cleaner and modular design**

---

##  Key Idea

Instead of a class creating its own dependencies, they are provided externally by the Spring container. This leads to better separation of concerns and more scalable applications.

---

## Summary

> Dependency Injection allows Spring to manage object creation and inject dependencies automatically, resulting in loosely coupled and maintainable code.
