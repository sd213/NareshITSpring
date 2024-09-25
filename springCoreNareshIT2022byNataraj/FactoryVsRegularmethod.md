# Factory Method vs Regular Method

To determine if a method is a **factory method** or a regular method, you can consider the following characteristics:

### 1. **Factory Method**
A **factory method** is a method used to create and return instances of a class, often used when:
- **Constructor visibility** is restricted (e.g., `private` or `protected` constructor).
- You want to control the object creation process or manage how objects are instantiated.

#### Characteristics of Factory Methods:
- **Static or instance method**: A factory method can be a `static` method (common for factory design patterns) or an instance method.
- **Return type**: The return type of a factory method is typically the class of the object being created (or a subclass).
- **Method name**: Factory methods usually follow naming conventions like `create`, `getInstance`, `newInstance`, `of`, `from`, etc.

#### Example of a Static Factory Method:
```java
public class LocalDateTimeFactory {
    // Static factory method
    public static LocalDateTime now() {
        return LocalDateTime.now();
    }
}
```
- **`now()` is a static factory method** that creates and returns an instance of `LocalDateTime`.

#### Example of an Instance Factory Method:
```java
public class ConnectionFactory {
    // Instance factory method
    public Connection createConnection() {
        // Return new connection object
        return new Connection();
    }
}
```
- **`createConnection()` is an instance factory method** that returns a new `Connection` object.

---

### 2. **Regular Method**
A **regular method** is any method that doesn't follow the factory method pattern. It may:
- Perform an action or modify object state.
- Return a value based on computations or internal data but not necessarily create a new object of the class.

#### Characteristics of Regular Methods:
- **Usually non-static** (although static methods can be regular methods as well).
- The return type is often not the same class type, and the method might return `void`, a primitive, or any other object type.
- **Naming**: Regular methods are named based on their function and often describe the action being performed (e.g., `getName()`, `calculateTotal()`).

#### Example of a Regular Method:
```java
public class Car {
    private String model;
    private int year;

    // Regular method
    public String getModel() {
        return model;
    }

    // Another regular method
    public int getYear() {
        return year;
    }
}
```
- **`getModel()` and `getYear()` are regular methods** that return internal properties of the `Car` class.

---

### Key Differences

| **Type of Method**   | **Characteristics**                                                                                 |
|----------------------|-----------------------------------------------------------------------------------------------------|
| **Factory Method**    | - Used to create and return instances of a class.                                                   |
|                      | - Can be `static` or instance method.                                                               |
|                      | - Often follows naming conventions like `create`, `getInstance`, `newInstance`, `of`, `from`.       |
|                      | - May return an interface or a subclass of the class.                                               |
|                      | - Controls object creation (e.g., Singleton, Prototype patterns).                                   |
| **Regular Method**    | - Used to perform an action, calculate a value, or manipulate internal state.                       |
|                      | - Usually returns a property, computed value, or modifies internal data.                            |
|                      | - Can return any type of data, including `void`, primitive types, or objects not related to object creation. |

---

### Identifying Factory Methods in Documentation

1. **Check Method Signature:**
   - **Factory methods** usually have a return type that matches the class (or an interface/subclass). For example:
     ```java
     public static MyClass createInstance();
     public Connection createConnection();
     ```
   - **Regular methods** can return any type, not necessarily related to object creation:
     ```java
     public String getModel();
     public int calculateSum();
     ```

2. **Check for Static Methods:**
   - Factory methods are often `static` but not always. A method that is `static` and returns a class instance could be a factory method.

3. **Naming Convention:**
   - Factory methods often use specific names like `create`, `getInstance`, `newInstance`, `of`, `from`, etc. Check for these keywords in the method name.

4. **Check Documentation:**
   - If you're unsure, consult the **Javadoc** or documentation of the method. Factory methods are typically documented to indicate that they create new instances.

---

### Real-World Example: `LocalDateTime.now()`

- **Factory Method**: `LocalDateTime.now()` is a static factory method that creates a new `LocalDateTime` instance representing the current date and time.
  
  ```java
  public static LocalDateTime now() {
      return new LocalDateTime();
  }
  ```

### Real-World Example: `java.util.Collections`

- **Factory Method**: `java.util.Collections` class contains many static factory methods to create collections, like `emptyList()`, `singletonList()`, etc.

  ```java
  public static <T> List<T> emptyList() {
      return (List<T>) EMPTY_LIST;
  }

  public static <T> List<T> singletonList(T o) {
      return new SingletonList<>(o);
  }
  ```

Both methods are examples of factory methods returning different types of collection objects.

---

### Conclusion:
- **Factory methods** are specifically designed to create and return instances of a class, often static and following certain naming conventions.
- **Regular methods** perform actions or calculations and may return any data type. They are not focused on object creation.
  
By looking at the method signature, naming conventions, and documentation, you can easily identify whether a method is a factory method or a regular method.