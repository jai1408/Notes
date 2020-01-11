## Spring Boot Notes

#### Annotations in Spring Boot

`@Component` is a generic stereotype for any Spring-managed component. `@Repository`, `@Service`, and `@Controlle`r are specializations of `@Component` for more specific use cases in the persistence, service, and presentation layers, respectively.

| Annotations   | Meaning  |
| ------------- |:-------------:|
| @Component    | generic stereotype for any Spring-managed component|
| @Repository   | stereotype for persistence Layer|
| @Service      | stereotype for service layer|
| @Controller   | stereotype for presentation layer (spring-mvc)|


***

#### First the Similarity

First point worth highlighting again is that with respect to scan-auto-detection and dependency injection for BeanDefinition all these annotations (viz., @Component, @Service, @Repository, @Controller) are the same. We can use one in place of another and can still get our way around.

#### Differences between @Component, @Repository, @Controller and @Service

##### @Component

This is a general-purpose stereotype annotation indicating that the class is a spring component.

What’s special about @Component
<context:component-scan> only scans @Component and does not look for @Controller, @Service and @Repository in general. They are scanned because they themselves are annotated with @Component.

Just take a look at @Controller, @Service and @Repository annotation definitions:

```
@Component
public @interface Service {
    ….
}
```
 
```
@Component
public @interface Repository {
    ….
}
```
 
```
@Component
public @interface Controller {
    …
}
```

Thus, it’s not wrong to say that @Controller, @Service and @Repository are special types of @Component annotation. <context:component-scan> picks them up and registers their following classes as beans, just as if they were annotated with @Component.

Special type annotations are also scanned, because they themselves are annotated with @Component annotation, which means they are also @Components. If we define our own custom annotation and annotate it with @Component, it will also get scanned with <context:component-scan>

#####@Repository

This is to indicate that the class defines a data repository.

What’s special about @Repository?

In addition to pointing out, that this is an Annotation based Configuration, @Repository’s job is to catch platform specific exceptions and re-throw them as one of Spring’s unified unchecked exception. For this, we’re provided with PersistenceExceptionTranslationPostProcessor, that we are required to add in our Spring’s application context like this:

<bean class="org.springframework.dao.annotation.PersistenceExceptionTranslationPostProcessor"/>

This bean post processor adds an advisor to any bean that’s annotated with @Repository so that any platform-specific exceptions are caught and then re-thrown as one of Spring’s unchecked data access exceptions.

##### @Controller

The @Controller annotation indicates that a particular class serves the role of a controller. The @Controller annotation acts as a stereotype for the annotated class, indicating its role.

What’s special about @Controller?

We cannot switch this annotation with any other like @Service or @Repository, even though they look same. The dispatcher scans the classes annotated with @Controller and detects methods annotated with @RequestMapping annotations within them. We can use @RequestMapping on/in only those methods whose classes are annotated with @Controller and it will NOT work with @Component, @Service, @Repository etc...

Note: If a class is already registered as a bean through any alternate method, like through @Bean or through @Component, @Service etc... annotations, then @RequestMapping can be picked if the class is also annotated with @RequestMapping annotation. But that's a different scenario.

##### @Service

@Service beans hold the business logic and call methods in the repository layer.

What’s special about @Service?

Apart from the fact that it's used to indicate, that it's holding the business logic, there’s nothing else noticeable in this annotation; but who knows, Spring may add some additional exceptional in future.

What else?

Similar to above, in the future Spring may add special functionalities for @Service, @Controller and @Repository based on their layering conventions. Hence, it's always a good idea to respect the convention and use it in line with layers.

***

#### Exception Handling
* The **@ControllerAdvice** is an annotation, to handle the exceptions globally
* The **@ExceptionHandler** is an annotation used to handle the specific exceptions and sending the custom responses to the client.

**ProductNotfoundException.java**
```
public class ProductNotfoundException extends RuntimeException {
   private static final long serialVersionUID = 1L;
}
```
**ProductExceptioController.java**
```
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;

@ControllerAdvice
public class ProductExceptionController {
   @ExceptionHandler(value = ProductNotfoundException.class)
   public ResponseEntity<Object> exception(ProductNotfoundException exception) {
      return new ResponseEntity<>("Product not found", HttpStatus.NOT_FOUND);
   }
}
```

***
####  Spring Boot - Enabling HTTPS
* Obtain the SSL certificate â€“ Create a self-signed certificate or get one from a Certificate Authority
* Enable HTTPS and 443 port

**Self-Signed Certificate**
```
keytool -genkey -alias tomcat -storetype PKCS12 -keyalg RSA -keysize 2048 -keystore keystore.p12 -validity 3650
Enter keystore password:
   Re-enter new password:
   What is your first and last name?
   [Unknown]:
   What is the name of your organizational unit?
   [Unknown]:
   What is the name of your organization?
   [Unknown]:
   What is the name of your City or Locality?
   [Unknown]:
   What is the name of your State or Province?
   [Unknown]:
   What is the two-letter country code for this unit?
   [Unknown]:
   Is CN = Unknown, OU=Unknown, O = Unknown, L = Unknown, ST = Unknown, C = Unknown correct?
   [no]: yes
```
**Configure HTTPS**
```
server.port: 443
server.ssl.key-store: keystore.p12
server.ssl.key-store-password: springboot
server.ssl.keyStoreType: PKCS12
server.ssl.keyAlias: tomcat
```
