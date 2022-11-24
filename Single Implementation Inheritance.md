*Inheritance* is one of the fundamental mechanisms for code reuse in OOP. It allows  
new classes to be derived from an existing class.
The new class (also called subclass,  subtype, derived class, child class) can inherit members from the old class (also called  superclass, supertype, base class, parent class). 

Subclass - superclass
Subtype - supertype
Derived class - Base class
Child class - parent class
also:
extended class (the same as subclass)

The subclass can add new behavior and  properties and, under certain circumstances, modify its inherited behavior.

In Java, [[implementation inheritance]] is achieved by extending classes (i.e., adding  
new fields and methods) and modifying inherited members.
If a superclass member is accessible by it's simple name in the subclass, this member is considered inherited. That means that private, overriden or hidden members are not inherited. Inheritance should not be confused with [[existence]] of such members in the state of the subclass object.