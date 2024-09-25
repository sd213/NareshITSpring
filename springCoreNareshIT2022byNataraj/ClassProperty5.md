# how a userdefined class inheriting no other class other than object super class gets property of Class object , is through has-A relationship  a  userdefined or any class gets

## In Java, every **user-defined class** that does not explicitly extend any other class **automatically inherits** from the `Object` class, which is the root class of all Java classes. This inheritance provides all classes, including user-defined ones, with a default **`Class` object** through Java's runtime system. However, this is not because of a **"has-A" relationship** but due to an inherent part of Java's **reflection mechanism**.

Let’s break this down:

### 1. **Inheritance from `Object` Class**:
   - If a user-defined class does not extend any other class, it implicitly extends the **`java.lang.Object`** class. 
   - Every class in Java is ultimately a subclass of `Object`, which is why all classes, even user-defined ones, inherit methods like `toString()`, `hashCode()`, and `equals()` from `Object`.
   - **Example**:
     ```java
     public class MyClass {
         // This is implicitly equivalent to:
         // public class MyClass extends Object { }
     }
     ```

### 2. **`Class` Object in Java**:
   - In Java, every class, whether it's a built-in class like `String` or a user-defined class like `MyClass`, has a corresponding **`Class` object** at runtime.
   - This **`Class` object** is created automatically by the Java Virtual Machine (JVM) when the class is loaded.
   - The **`Class` object** is part of the **Reflection API** and contains metadata about the class, including methods, fields, constructors, etc.

### 3. **How Does a Class Get Its `Class` Object?**
   - **Not through a "has-A" relationship**: The `Class` object for a class is **not a field** or a member inside the class. It’s not as if the class contains an instance of the `Class` type. 
   - Instead, every class in Java **automatically** gets associated with a **`Class` object** at runtime when the JVM loads that class into memory. The JVM internally manages this association.
   - This happens due to the **JVM's class-loading mechanism**. When the class is loaded into memory, the JVM automatically creates an instance of `Class` that contains all the metadata about the class.

### 4. **Implicit Mechanism of `Class` Object Creation**:
   - When any class (including user-defined classes) is loaded by the JVM, it is automatically associated with a **`Class` object**.
   - This is an internal mechanism, so it’s not a case of an explicit **"has-A" relationship** where the class contains or holds a reference to the `Class` object. Instead, it's managed by the JVM.

### Example of a User-Defined Class Getting a `Class` Object:

```java
public class MyClass {
    public void myMethod() {
        System.out.println("This is my method.");
    }

    public static void main(String[] args) {
        // Accessing the Class object of MyClass
        Class<?> myClassObject = MyClass.class;

        // Printing the name of the class
        System.out.println("Class name: " + myClassObject.getName());
    }
}
```

### Output:
```
Class name: MyClass
```

### 5. **The Relationship Between a Class and Its `Class` Object**:
   - The **`Class` object** is not a member (has-A) of the user-defined class; rather, it is an internal object that the JVM maintains for each class loaded into memory.
   - Every class, whether user-defined or not, automatically gets its **`Class` object** from the JVM without any explicit declaration.
   - This is part of the **Reflection API** in Java. The `.class` syntax provides a way to access this metadata **at runtime**, but the relationship between a class and its `Class` object is a JVM-managed **association**, not an explicit **composition** or **"has-A" relationship**.

### 6. **Summary**:
   - A user-defined class inherits from the `Object` class, which is the root of all classes in Java.
   - Every class in Java has an associated **`Class` object** that the JVM creates and maintains when the class is loaded.
   - The **`Class` object** provides metadata about the class but is **not part of the class in a "has-A" relationship**. Instead, it's automatically created and managed by the JVM’s class-loading mechanism.
   - This is a key part of Java’s **reflection mechanism**, allowing developers to inspect classes, methods, fields, etc., at runtime.
   
   