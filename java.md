#### Exception Handling in overriding

1. If SuperClass does not declare an exception, then the SubClass can only declare unchecked exceptions, but not the checked exceptions.
2. If SuperClass declares an exception, then the SubClass can only declare the child exceptions of the exception declared by the SuperClass, but not any other exception.
3. If SuperClass declares an exception, then the SubClass can declare without exception.

#### Method Overriding with Access Modifiers

Their is Only one rule while doing Method overriding with Access modifiers i.e.   
`If you are overriding any method, overridden method (i.e. declared in subclass) must not be more restrictive.`  
**Access modifier restrictions in decreasing order:**
`private>default>protected>public`

#### Covariant return types
Java 5.0 onwards it is possible to have different return type for a overriding method in child class, but child’s return type should be sub-type of parent’s return type. Overriding method becomes variant with respect to return type.
***
#### An interface can have six different things:
1. Constant variables
2. Abstract methods
3. Default methods
4. Static methods
5. Private methods
6. Private Static methods
