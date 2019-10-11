## Spring Boot Notes

#### Exception Handling
* The @ControllerAdvice is an annotation, to handle the exceptions globally
* The @ExceptionHandler is an annotation used to handle the specific exceptions and sending the custom responses to the client.

ProductNotfoundException.java
```
public class ProductNotfoundException extends RuntimeException {
   private static final long serialVersionUID = 1L;
}
```
ProductExceptioController.java
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
* Obtain the SSL certificate – Create a self-signed certificate or get one from a Certificate Authority
* Enable HTTPS and 443 port

Self-Signed Certificate
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
Configure HTTPS
```
server.port: 443
server.ssl.key-store: keystore.p12
server.ssl.key-store-password: springboot
server.ssl.keyStoreType: PKCS12
server.ssl.keyAlias: tomcat
```
