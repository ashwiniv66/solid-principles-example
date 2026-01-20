# solid-principles-example -  Quick Notes 
Here’s a **clean, interview-ready README** for the **SOLID Principles**, suitable for a **Java / Spring Boot developer** like you. You can directly use this in GitHub 📘

---

# SOLID Principles

## Overview

**SOLID** is a set of five object-oriented design principles that help developers write **clean, maintainable, scalable, and testable code**.
These principles are widely used in **Java**, **Spring Boot**, and **microservices architectures**.

**SOLID stands for:**

* **S** – Single Responsibility Principle
* **O** – Open/Closed Principle
* **L** – Liskov Substitution Principle
* **I** – Interface Segregation Principle
* **D** – Dependency Inversion Principle

---

## 1. Single Responsibility Principle (SRP)

> A class should have **only one reason to change**.

### ❌ Bad Example

```java
class UserService {
    void saveUser(User user) {}
    void sendEmail(User user) {}
}
```

### ✅ Good Example

```java
class UserService {
    void saveUser(User user) {}
}

class EmailService {
    void sendEmail(User user) {}
}
```

### ✔ Benefits

* Easier maintenance
* Better readability
* Simplified testing

---

## 2. Open/Closed Principle (OCP)

> Software entities should be **open for extension but closed for modification**.

### ❌ Bad Example

```java
class DiscountService {
    double calculate(String type) {
        if(type.equals("STUDENT")) return 10;
        if(type.equals("EMPLOYEE")) return 20;
        return 0;
    }
}
```

### ✅ Good Example

```java
interface Discount {
    double calculate();
}

class StudentDiscount implements Discount {
    public double calculate() { return 10; }
}

class EmployeeDiscount implements Discount {
    public double calculate() { return 20; }
}
```

### ✔ Benefits

* Avoids breaking existing code
* Supports scalability

---

## 3. Liskov Substitution Principle (LSP)

> Subclasses must be **substitutable for their base classes**.

### ❌ Bad Example

```java
class Bird {
    void fly() {}
}

class Penguin extends Bird {
    void fly() {
        throw new UnsupportedOperationException();
    }
}
```

### ✅ Good Example

```java
interface Bird {}

interface FlyingBird extends Bird {
    void fly();
}

class Sparrow implements FlyingBird {
    public void fly() {}
}

class Penguin implements Bird {}
```

### ✔ Benefits

* Prevents runtime errors
* Improves design correctness

---

## 4. Interface Segregation Principle (ISP)

> Clients should not be forced to depend on interfaces they do not use.

### ❌ Bad Example

```java
interface Worker {
    void work();
    void eat();
}
```

### ✅ Good Example

```java
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}
```

### ✔ Benefits

* Smaller, cleaner interfaces
* Better flexibility

---

## 5. Dependency Inversion Principle (DIP)

> High-level modules should not depend on low-level modules.
> Both should depend on abstractions.

### ❌ Bad Example

```java
class Car {
    Engine engine = new Engine();
}
```

### ✅ Good Example

```java
interface Engine {
    void start();
}

class PetrolEngine implements Engine {
    public void start() {}
}

class Car {
    private Engine engine;

    Car(Engine engine) {
        this.engine = engine;
    }
}
```

### ✔ Benefits

* Loose coupling
* Easier unit testing
* Supports Spring’s Dependency Injection

