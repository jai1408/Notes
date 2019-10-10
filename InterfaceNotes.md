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
* **class MyClass** implements Alpha   
> Beta Is the version by Alpha or the version by Beta used by MyClass? **Error will occur**
> Consider interface Beta extends Alpha. 
> Which version of the default method is used? **Beta’s version of reset( ) will be used**
> what if MyClass provides its own implementation of the method? **MyClass version is used. Both default methods are overridden by class           implementation of method**


* Static interface methods are not inherited by either an implementing
class or a sub interface.


* Illegal combination of modifiers for the interface method reset; 
only one of abstract, default, or static permitted
