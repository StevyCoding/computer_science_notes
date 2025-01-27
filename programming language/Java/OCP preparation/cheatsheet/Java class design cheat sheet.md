

Here's a more polished and formatted version of your cheat sheet for Java Class Design, optimized for clarity and structure:

---

### Cheat Sheet: Java Class Design for OCP 17 Exam

---

#### 1. Key Principles of Class Design

- **Encapsulation**: Use private fields with public getters/setters.
- **Inheritance**: Extend classes and override methods where appropriate.
- **Polymorphism**: Use abstract classes/interfaces to define shared behavior.
- **Cohesion**: Each class should have a single responsibility.
- **Coupling**: Aim for low coupling between classes.

---

#### 2. Access Modifiers

|Modifier|Class|Package|Subclass|World|
|---|---|---|---|---|
|`public`|✅|✅|✅|✅|
|`protected`|✅|✅|✅|❌|
|(default)|✅|✅|❌|❌|
|`private`|✅|❌|❌|❌|

---

#### 3. Abstract Classes vs. Interfaces

|Feature|Abstract Class|Interface|
|---|---|---|
|Can have instance fields?|✅ Yes|❌ No|
|Default implementation?|✅ Yes (methods)|✅ Yes (`default`)|
|Multiple inheritance allowed?|❌ No|✅ Yes|
|Access modifiers for methods|`public`, `protected`|`public` only|

---

#### 4. Rules for `final` Keyword

- **Final Class**: Cannot be extended.
    
    ```java
    public final class FinalClass {}
    ```
    
- **Final Method**: Cannot be overridden.
    
    ```java
    public final void myMethod() {}
    ```
    
- **Final Variable**: Value cannot be reassigned after initialization.
    
    ```java
    final int MAX = 10;
    ```
    

---

#### 5. Overloading vs. Overriding

|Feature|Overloading|Overriding|
|---|---|---|
|Method signature|Different|Same|
|Return type|Can differ|Must be same/subtype|
|Access level|Can differ|Must not reduce visibility|
|`static` methods allowed|✅ Yes|❌ No|
|Runtime or Compile Time?|Compile Time|Runtime|

---

#### 6. Static and Instance Members

- **Static Methods**:
    - Accessed without an instance.
    - Cannot access instance variables directly.
- **Instance Methods**:
    - Require an object to be invoked.
    - Can access static and instance variables.

---

#### 7. Nested Classes

- **Static Nested Class**:
    - Does not have access to the outer class’s instance variables.
- **Inner Class**:
    
    - Can access the outer class’s members.
    
    ```java
    class Outer {
        class Inner {}
    }
    ```
    
- **Local Class**:
    - Declared within a method or block.
- **Anonymous Class**:
    
    - Created during instantiation of a class or interface.
    
    ```java
    Runnable r = new Runnable() {
        public void run() {}
    };
    ```
    

---

#### 8. Important Design Patterns

- **Singleton**:
    
    - Ensure a class has only one instance.
    
    ```java
    public class Singleton {
        private static Singleton instance = new Singleton();
        private Singleton() {}
        public static Singleton getInstance() {
            return instance;
        }
    }
    ```
    
- **Factory**:
    - Create objects without specifying the exact class.
- **Builder**:
    - Simplify object construction.

---

#### 9. Object Class Methods

|Method|Purpose|
|---|---|
|`equals(Object obj)`|Compares objects for equality.|
|`hashCode()`|Returns the hash code of an object.|
|`toString()`|Returns a string representation.|
|`clone()`|Creates a copy of the object.|
|`finalize()`|Called before garbage collection.|

---

#### 10. Sealed Classes

- Restrict which classes can extend/implement the class/interface.
- Introduced in Java 17.
    
    ```java
    public sealed class Shape permits Circle, Rectangle {}
    public final class Circle extends Shape {}
    public non-sealed class Rectangle extends Shape {}
    ```
    

---

#### 11. Best Practices

- Favor composition over inheritance.
- Use interfaces for type definitions.
- Minimize the use of mutable fields.
- Avoid circular dependencies.
- Use meaningful class and method names.

---

Let me know if you'd like this formatted as a PDF carousel!