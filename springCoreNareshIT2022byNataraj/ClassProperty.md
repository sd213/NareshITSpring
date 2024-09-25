## Class c1 = System.class  ; class is  the static property  of type java.lang.Class in System class




### Yes, in the statement `Class c1 = System.class;`, you are accessing the `class` property of the `System` class. This is a special type of property in Java that refers to the **class literal** and is available for all classes. The property `class` is **implicitly static** in every Java class, and it is of type `java.lang.Class<?>`.

### Explanation:

1. **`System.class`**:
   - Every class in Java has an implicit `class` property that holds a reference to the **`Class` object** representing the class itself.
   - In the case of `System.class`, it refers to the `Class` object associated with the `System` class.

2. **`Class c1 = System.class;`**:
   - The variable `c1` is of type `Class`, and it stores the `Class` object representing the `System` class.
   - The type of `System.class` is `java.lang.Class<System>`, which means it is a `Class` object associated with the `System` class.

3. **`Class` in Java**:
   - The `Class` class in Java is a part of the **Reflection API**, which allows Java programs to inspect and manipulate classes at runtime.
   - The `Class` object provides metadata about the class it represents, such as its methods, constructors, fields, etc.

### Example:

```java
public class Example {
    public static void main(String[] args) {
        // Get the Class object for System class
        Class<?> systemClass = System.class;

        // Print the name of the class
        System.out.println("Class name: " + systemClass.getName());

        // Check if it represents an interface
        System.out.println("Is interface: " + systemClass.isInterface());

        // Check if it represents a primitive type
        System.out.println("Is primitive: " + systemClass.isPrimitive());

        // Check if it represents an array
        System.out.println("Is array: " + systemClass.isArray());
    }
}
```

### Output:
```
Class name: java.lang.System
Is interface: false
Is primitive: false
Is array: false
```

### Key Concepts:
- **`Class<?>`**: 
   - The wildcard `?` in `Class<?>` indicates that the class type is not specified. You can use `Class<T>` when you know the exact type.
- **Reflection**:
   - By accessing the `Class` object of a class, you can use reflection to obtain details about the class at runtime.
- **Static nature**:
   - The `class` property is static because you don't need an instance of the class to access it. It belongs to the class itself, not to instances of the class.

### Example with Reflection:
Using the `Class` object, you can retrieve metadata about the class, such as methods, fields, constructors, etc.

```java
import java.lang.reflect.Method;

public class ReflectionExample {
    public static void main(String[] args) {
        // Get the Class object for the System class
        Class<System> systemClass = System.class;

        // Get all methods of the System class
        Method[] methods = systemClass.getMethods();

        // Print the method names
        System.out.println("Methods in System class:");
        for (Method method : methods) {
            System.out.println(method.getName());
        }
    }
}
```

### Output:
```
Methods in System class:
getProperties
getProperty
setProperty
clearProperty
...
```

### Summary:
- **`System.class`** returns the `Class` object representing the `System` class.
- The `class` keyword can be used to access the `Class` object for any Java class.
- You can use the `Class` object for reflective operations, like retrieving methods, fields, and constructors.

