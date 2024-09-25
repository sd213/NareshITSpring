# is Class  is a builtin static property of type java.lang.Class


## Yes, **`Class`** is a built-in **static property** that is implicitly available for all classes in Java. It is of type `java.lang.Class<?>`. Here's the breakdown:

### Key Points:

1. **`Class` as a Built-in Property**:
   - Every class in Java has an implicit static property called `class`, which gives access to its associated `java.lang.Class` object.
   - This `class` property is not explicitly declared in the class itself but is automatically available for every class.

2. **Type of `class` Property**:
   - The type of this property is `java.lang.Class`, and more specifically, `Class<?>` (which is a generic form indicating a class of an unknown type).
   - For example, `System.class` would be of type `Class<System>`.

3. **Static Nature**:
   - The `class` property is **static**, meaning it belongs to the class itself, not to any instance of the class. You can access it directly through the class name, e.g., `System.class`.
   
4. **Purpose of `Class` Object**:
   - The `Class` object represents the metadata of a class and provides methods to inspect its details, such as its fields, methods, constructors, and more.
   - It is a part of the **Java Reflection API**.

### Example:

```java
public class Example {
    public static void main(String[] args) {
        // Get the Class object for System class using the implicit class property
        Class<System> systemClass = System.class;

        // Print the name of the class
        System.out.println("Class name: " + systemClass.getName()); // Output: java.lang.System
    }
}
```

### Explanation:
- **`System.class`**: This is the **implicit static property** that returns the `Class` object for the `System` class. It is of type `Class<System>`.
- The `class` property is available for every Java class, whether it's `System`, `String`, or even a user-defined class.

### Built-in Nature of `Class` Property:
- Every Java class has this **`class` property** automatically generated, even if you do not declare it. You can access it for both built-in classes and user-defined classes.

### Example with User-Defined Class:

```java
public class MyClass {
    public static void main(String[] args) {
        // Access the Class object of MyClass using MyClass.class
        Class<MyClass> myClassObj = MyClass.class;

        // Print class name
        System.out.println("Class name: " + myClassObj.getName()); // Output: MyClass
    }
}
```

### Reflection with the `Class` Object:

Once you have the `Class` object (like `MyClass.class` or `System.class`), you can perform reflection:

```java
public class ReflectionExample {
    public static void main(String[] args) {
        // Get Class object for String class
        Class<String> stringClass = String.class;

        // Print methods declared in String class
        System.out.println("Methods in String class:");
        for (Method method : stringClass.getDeclaredMethods()) {
            System.out.println(method.getName());
        }
    }
}
```

### Summary:
- The `class` is an **implicitly available static property** for every Java class.
- It is of type `java.lang.Class<?>`, and it gives access to the `Class` object representing that class.
- This property allows reflection and access to class metadata.