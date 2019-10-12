#Inteface Notes

* Variables can be declared inside of interface declarations.   
They are implicitly final and static, meaning they cannot be changed by the implementing
class.   
They must also be initialized. All methods and variables are implicitly public.


* Any class that implements an interface must implement all methods required by that interface,
including any that are inherited from other interfaces.


* When you implement an interface method, it must be declared as public.


* The release of JDK 8 has changed this by adding a new capability to interface called the default method.


* It is still not possible to create an instance of an interface by itself. It must be implemented by
a class. Therefore, even though, beginning with JDK 8, an interface can define default
methods, the interface must still be implemented by a class if an instance is to be created.


* There is still a key difference between a class and an interface: a class can maintain state information
(especially through the use of instance variables), but an interface cannot


* **interface Alpha** default implementation of reset().
* **interface Beta** default implementation of reset().
* **class MyClass** implements Alpha, Beta   
> Is the version by Alpha or the version by Beta used by MyClass? **Error will occur**  
> Consider interface Beta extends Alpha.  
> Which version of the default method is used? **Beta version of reset( ) will be used**  
> what if MyClass provides its own implementation of the method? **MyClass version is used. Both default methods are overridden by class           implementation of method**


* Static interface methods are not inherited by either an implementing
class or a sub interface.


* Illegal combination of modifiers for the interface method reset; 
only one of abstract, default, or static permitted

### Difference between Interface and Abstract class

* The abstract keyword is used to create an abstract class whereas interface keyword is used to create an interface.

* The variable of an abstract class can have final, non-final, static and non-static variables whereas the variable of an interface should be always public static final.

* we can achieve multiple inheritances by using interface whereas with an abstract class it is not possible as multiple inheritance is not supported by java.

* An interface can�t have a constructor within it whereas the abstract class can have a constructor within it

### Exception Handling in overriding

1. If SuperClass does not declare an exception, then the SubClass can only declare unchecked exceptions, but not the checked exceptions.
2. If SuperClass declares an exception, then the SubClass can only declare the child exceptions of the exception declared by the SuperClass, but not any other exception.
3. If SuperClass declares an exception, then the SubClass can declare without exception.

### Method Overriding with Access Modifiers

Their is Only one rule while doing Method overriding with Access modifiers i.e.   
`If you are overriding any method, overridden method (i.e. declared in subclass) must not be more restrictive.`  
**Access modifier restrictions in decreasing order:**
`private>default>protected>public`

### Covariant return types
Java 5.0 onwards it is possible to have different return type for a overriding method in child class, but child’s return type should be sub-type of parent’s return type. Overriding method becomes variant with respect to return type.

***
### An interface can have six different things:
1. Constant variables
2. Abstract methods
3. Default methods
4. Static methods
5. Private methods
6. Private Static methods

### Rules For using Private Methods in Interfaces

* Private interface method cannot be abstract and no private and abstract modifiers together.
* Private method can be used only inside interface and other static and non-static interface methods.
* Private non-static methods cannot be used inside private static methods.
* We should use private modifier to define these methods and no lesser accessibility than private modifier.



