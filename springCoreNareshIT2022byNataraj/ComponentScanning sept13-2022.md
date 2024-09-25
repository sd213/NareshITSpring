# Different way of doing component scan in xml and annotation

## In Spring, **component scanning** is used to automatically detect and register beans (classes annotated with `@Component`, `@Service`, `@Repository`, `@Controller`, etc.) in the Spring application context. Component scanning can be done both in **XML** and using **annotations** in Java.

Here’s a detailed guide to performing component scanning in both ways:

## 1. **Component Scanning Using XML Configuration**

In XML configuration, component scanning is done using the `<context:component-scan>` element, where you specify the base package(s) to scan for components.

### Example of XML-based Component Scanning

```xml
<!-- applicationContext.xml -->
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="
           http://www.springframework.org/schema/beans 
           http://www.springframework.org/schema/beans/spring-beans.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context.xsd">

    <!-- Component scanning -->
    <context:component-scan base-package="com.example.service" />
</beans>
```

### Explanation:
- The `base-package` attribute specifies the package where Spring should start scanning for classes annotated with `@Component`, `@Service`, `@Repository`, `@Controller`, etc.
- You can provide multiple base packages as a comma-separated list:
  
  ```xml
  <context:component-scan base-package="com.example.service, com.example.repository" />
  ```

- You can exclude specific classes or packages using the `exclude-filter` option, or include specific classes with `include-filter`.

#### Example of Filtering Components in XML

```xml
<context:component-scan base-package="com.example">
    <!-- Exclude classes annotated with @Controller -->
    <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller" />
</context:component-scan>
```

## 2. **Component Scanning Using Annotations**

In Java-based configuration, component scanning is done using the `@ComponentScan` annotation in a configuration class. The `@ComponentScan` annotation is used on a class annotated with `@Configuration`.

### Example of Annotation-based Component Scanning

```java
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan(basePackages = "com.example.service")
public class AppConfig {
    // Other @Bean definitions can go here
}
```

### Explanation:
- `@ComponentScan(basePackages = "com.example.service")` tells Spring to scan the `com.example.service` package for components.
- Similar to XML, you can specify multiple packages using an array:
  
  ```java
  @ComponentScan(basePackages = {"com.example.service", "com.example.repository"})
  ```

- You can also use **filters** to include or exclude specific components.

#### Example of Filtering Components in Annotation-based Configuration

```java
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.FilterType;
import org.springframework.stereotype.Controller;

@Configuration
@ComponentScan(
    basePackages = "com.example",
    excludeFilters = @ComponentScan.Filter(type = FilterType.ANNOTATION, value = Controller.class)
)
public class AppConfig {
    // Other @Bean definitions can go here
}
```

### Different Ways of Component Scanning in Annotations

- **Scanning specific types**: You can use `FilterType` to specify different types of components to scan or exclude.

```java
@ComponentScan(
    basePackages = "com.example",
    includeFilters = @ComponentScan.Filter(type = FilterType.ASSIGNABLE_TYPE, value = MySpecificClass.class)
)
public class AppConfig {
}
```

- **Using `@SpringBootApplication`**: In Spring Boot applications, the `@SpringBootApplication` annotation automatically enables component scanning for the package in which the main class resides, and all sub-packages under it.

```java
@SpringBootApplication // Combines @Configuration, @EnableAutoConfiguration, and @ComponentScan
public class MySpringBootApp {
    public static void main(String[] args) {
        SpringApplication.run(MySpringBootApp.class, args);
    }
}
```

### 3. **Comparison Between XML and Annotation-based Component Scanning**

| Aspect                        | XML Configuration                          | Annotation-based Configuration                 |
|-------------------------------|--------------------------------------------|------------------------------------------------|
| **Syntax**                     | `<context:component-scan>` in XML          | `@ComponentScan` in Java-based configuration   |
| **Configuration Location**     | External XML file                          | Within a Java class                            |
| **Type Safety**                | Not type-safe (typos in package names)      | Fully type-safe with IDE support for refactoring |
| **Filters**                    | Can filter based on annotations, types, etc. | Can filter using `@ComponentScan.Filter`        |
| **Customization**              | XML-based approach allows externalized configuration | Java-based is more concise and integrates with the code |
| **Ease of Use**                | Older approach, less common in modern Spring apps | More common in modern Spring apps              |

### 4. **Combining XML and Annotation-based Component Scanning**

You can combine XML and annotation-based component scanning. For example, you may define some beans in XML and use Java configuration for component scanning.

```xml
<!-- XML configuration -->
<context:component-scan base-package="com.example.service" />
<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource">
    <!-- Data source configuration -->
</bean>
```

```java
@Configuration
@ImportResource("classpath:applicationContext.xml")
@ComponentScan(basePackages = "com.example.repository")
public class AppConfig {
}
```

### Conclusion

- **XML-based configuration** is useful for legacy systems or where externalized configuration is desired.
- **Annotation-based configuration** is preferred in modern applications for its simplicity, type safety, and IDE support.
- Both methods can be used together in the same application if needed, but annotation-based configuration is the recommended approach for most new Spring applications.