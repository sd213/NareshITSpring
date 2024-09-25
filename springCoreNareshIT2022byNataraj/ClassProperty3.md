## what is this property .class of Java class contains

In Java, the **`.class`** property of a class is a built-in, implicit **static property** that provides access to a **`Class` object** representing the class it belongs to. This `Class` object is part of Java's **Reflection API** and contains metadata about the class, such as its methods, constructors, fields, superclass, interfaces, etc.

Here’s a more detailed breakdown of what the `.class` property contains:

### 1. **Class Metadata**:
   - **Name of the Class**: 
     - The `Class` object contains the name of the class, which can be accessed via `getName()`.
   - **Modifiers**:
     - You can check if the class is public, abstract, final, etc. using methods like `getModifiers()` and `Modifier.toString()`.
   - **Package Information**:
     - The package to which the class belongs can be retrieved using `getPackage()`.

### 2. **Superclass**:
   - The `.class` property contains information about the **superclass** (the parent class) of the class. This can be accessed with the `getSuperclass()` method.

### 3. **Methods**:
   - The `.class` property gives access to all the **methods** of the class, both declared and inherited. These can be accessed using methods like `getMethods()` and `getDeclaredMethods()`.

### 4. **Fields**:
   - It contains information about the **fields** (variables) defined in the class, including both static and instance fields. You can access these using `getFields()` or `getDeclaredFields()`.

### 5. **Constructors**:
   - The `.class` property also provides details about the **constructors** of the class. You can access these via the `getConstructors()` or `getDeclaredConstructors()` methods.

### 6. **Interfaces**:
   - The `Class` object provides information about all the **interfaces** the class implements using `getInterfaces()`.

### 7. **Annotations**:
   - It contains information about **annotations** applied to the class, methods, fields, or constructors, which can be accessed using `getAnnotations()` or `getDeclaredAnnotations()`.

### 8. **Nested Classes**:
   - If the class contains **inner classes** or **nested static classes**, the `.class` property provides access to them using `getClasses()` or `getDeclaredClasses()`.

### Example of Accessing Class Metadata Using `.class` Property:

```java
import java.lang.reflect.Method;
import java.lang.reflect.Field;
import java.lang.reflect.Constructor;

public class ReflectionDemo {
    public static void main(String[] args) {
        // Obtain the Class object for the String class
        Class<String> stringClass = String.class;

        // Get the name of the class
        System.out.println("Class Name: " + stringClass.getName());

        // Get the superclass of the class
        System.out.println("Superclass: " + stringClass.getSuperclass().getName());

        // Get the declared methods of the class
        Method[] methods = stringClass.getDeclaredMethods();
        System.out.println("\nMethods:");
        for (Method method : methods) {
            System.out.println(method.getName());
        }

        // Get the declared fields of the class
        Field[] fields = stringClass.getDeclaredFields();
        System.out.println("\nFields:");
        for (Field field : fields) {
            System.out.println(field.getName());
        }

        // Get the constructors of the class
        Constructor<?>[] constructors = stringClass.getConstructors();
        System.out.println("\nConstructors:");
        for (Constructor<?> constructor : constructors) {
            System.out.println(constructor);
        }
    }
}
```

### Output (Sample):
```
Class Name: java.lang.String
Superclass: java.lang.Object

Methods:
equals
hashCode
toString
charAt
...

Fields:
serialVersionUID
value
coder
...

Constructors:
public java.lang.String()
public java.lang.String(byte[])
public java.lang.String(char[])
...
```

### Key Methods Available on `Class` Object:
- **`getName()`**: Returns the name of the class.
- **`getSuperclass()`**: Returns the `Class` object representing the superclass.
- **`getMethods()` / `getDeclaredMethods()`**: Returns the methods of the class.
- **`getFields()` / `getDeclaredFields()`**: Returns the fields of the class.
- **`getConstructors()` / `getDeclaredConstructors()`**: Returns the constructors of the class.
- **`getInterfaces()`**: Returns the interfaces implemented by the class.
- **`getAnnotations()` / `getDeclaredAnnotations()`**: Returns annotations present in the class.

### Summary:
The `.class` property contains a **`Class` object** that provides detailed metadata about the class, including its name, methods, fields, constructors, interfaces, superclass, and annotations. This `Class` object is fundamental for Java's **Reflection API**, allowing you to inspect and manipulate the class structure at runtime.