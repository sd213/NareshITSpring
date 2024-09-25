##  Class c1 = App1.class .  here how c1 referencing to  Class Object

In the statement `Class c1 = App1.class;`, the variable `c1` is referencing a **`Class` object** that represents the **`App1` class**. Here’s a detailed explanation of how `c1` is referencing the **`Class` object**:

### 1. **`App1.class`**:
   - The **`.class`** property is a **built-in static property** that is available for every class in Java. 
   - When you write `App1.class`, it returns a **`Class` object** that represents the `App1` class.
   - The **`Class` object** holds the metadata about the `App1` class, such as:
     - The class name (`App1`)
     - The methods
     - The fields
     - The constructors
     - The superclass
     - The implemented interfaces

### 2. **What is `Class` in Java?**
   - The `Class` in Java is part of the **Reflection API** and represents the blueprint or structure of a class.
   - **`Class`** itself is a class in Java (`java.lang.Class`), and when you reference a class using `.class`, you get an object of type `Class`.
   - The `Class` object contains metadata that you can inspect at runtime using reflection.

### 3. **How `c1` references the `Class` object:**
   - In `Class c1 = App1.class;`, the **`App1.class`** expression provides a **reference** to the `Class` object that represents the `App1` class.
   - The **`c1` variable** is of type `Class`, and it is assigned the `Class` object of `App1` returned by `App1.class`.
   - This means that `c1` now holds the **reference** to the `Class` object for `App1`. 
   - Using this reference (`c1`), you can perform operations like inspecting the class’s methods, fields, and constructors, or even creating new instances of `App1` via reflection.

### 4. **The `Class` Object Representation:**
   - The `Class` object referenced by `c1` contains **metadata** about the `App1` class. This metadata includes:
     - **Class name** (fully qualified name like `App1` or `com.example.App1`)
     - **Superclass** (the parent class of `App1`)
     - **Declared methods** (methods defined in `App1`)
     - **Fields** (variables declared in `App1`)
     - **Annotations** (annotations applied to `App1`)
     - **Constructors** (constructors defined in `App1`)
     - **Interfaces** (interfaces implemented by `App1`)

### Example:

```java
public class App1 {
    private int id;
    private String name;

    public App1(int id, String name) {
        this.id = id;
        this.name = name;
    }

    public void displayInfo() {
        System.out.println("ID: " + id + ", Name: " + name);
    }

    public static void main(String[] args) {
        // Get the Class object for App1 using App1.class
        Class<App1> c1 = App1.class;

        // Print the class name
        System.out.println("Class name: " + c1.getName());  // Output: App1

        // Get the superclass of App1
        System.out.println("Superclass: " + c1.getSuperclass().getName());  // Output: java.lang.Object

        // Get the methods of App1
        Method[] methods = c1.getDeclaredMethods();
        System.out.println("\nDeclared Methods in App1:");
        for (Method method : methods) {
            System.out.println(method.getName());  // Output: displayInfo
        }
    }
}
```

### Output:
```
Class name: App1
Superclass: java.lang.Object

Declared Methods in App1:
displayInfo
```

### Explanation:
- **`App1.class`**: This returns the **`Class` object** for the `App1` class.
- **`c1`**: Now holds the reference to this `Class` object.
- Using `c1`, we access and print the class name (`App1`), the superclass (`java.lang.Object`), and the methods defined in `App1` (e.g., `displayInfo`).

### 5. **How `c1` is Referencing the Class Object**:
- **`App1.class`**: Provides the **`Class` object** representing the `App1` class.
- **`c1`**: Holds a reference to this `Class` object. It allows you to perform various reflection operations on the `App1` class, such as inspecting methods, fields, and constructors, or dynamically creating instances of `App1` at runtime.

### Summary:
- The `.class` property in `App1.class` is referencing a **`Class` object** that contains metadata about the `App1` class.
- **`c1`** holds a reference to this **`Class` object**, which allows you to interact with the class's structure at runtime using the Reflection API.
