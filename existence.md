extract from c++ discussion:
https://stackoverflow.com/questions/14270631/do-sub-classes-really-inherit-private-member-variables

Physically, every single member( including member functions) of base class goes into the subclass. Doesn't matter if they are private. Doesn't matter if you inherit them publically/protected-ly/privately. So in your example, `yourClass` contains all three of `getMyVariable()`, `setMyVariable()` and `myVariable`. All this is pretty simple, okay?

What matters is how we can access them. It is like when a file is deleted on your system. So, you should first understand the difference between a member being not there and a member being there but inaccessible. Assume for now that all inheritance takes place publically. Then, all public members of base class are public in derived class, protected members are protected and private members are inaccessible. They are inaccessible and not non-existent because there can be some member functions in protected and public sections in base class which access the private members of base class. Thus, we need all those private members of base which are accessed by public and protected member functions of base, for their functionality. Since there is no way that we can determine which member is needed by which member function in a simple manner, we include all private members of the base class in derived class. All this simply means that in a derived class, a private member can be modified by only through the base class' member functions.

Note: every private member has to be accessed, directly or indirectly (through another private member function which in turn is called by a public/protected member function) by a public/protected meber function, else it has no use.

So, we know till now that a private member variable of base class has its use in derived class i.e. for the functionality of its public/protected member functions. But they can't be accessed directly in base class.

Now, we turn our attention to private/public inheritance. For public inheritance, it means that all the accessible members of base class (that is, the public and protected members) can not be at a level more permissive than public. Since, public is the most permissive level, public and protected members remain public. But at protected and private inheritance, both become protected and private in the derived class, respectively. Inthe latter case, since all these members are private, they can't be accessed further in the hierarchy chain, but can be accessed by the given derived class all the same.

Thus, the level of each base class member in derived class is the lesser of their level in derived class () and the type of inheritance (public/protected/private).

Same concept applies to the functions outside the class. For them private and protected members are inaccessible but they do exist and can be accessed by the public member functions.

And taking your case as a final example, `setMyvariable()` and `getMyVariable()` can access `myVariable` in the derived class. But no function specified in derived class can access `myVariable`. Modifying your class:

```cpp
class myClass
{
public:
  void setMyVariable();
  int getMyVariable();
private:
  int myVariable;
};

class yourClass : public myClass
{
public:
  // void yourFunction() { myVariable = 1; }
  /*Removing comment creates error; derived class functions can't access myVariable*/
};
```

Further: you can add exceptions to the type of inheritance too e.g. a private inheritance except a member made public in derived class. But that is another question altogether.



Extract from Khalid Mukhal chapter 7.1:

Private members of the superclass are not inherited by the subclass and can only  
be indirectly accessed. The private field indicator of the superclass Light is not  
inherited, but exists in the subclass object and is indirectly accessible:

```Java
class Light {
private boolean indicator; 
public boolean isOn() { return indicator; }
}


class TubeLight extends Light {
public void printInfo() {
// System.out.println("Indicator: " + indicator); // Not Inherited.
System.out.println("Indicator: " + isOn()); // Inherited.
}
}
```

I think indirectly accessible means "by public, protected or package private methods of the base class that use the private member"

example:

```Java
public class A {  
    private int privateN4= 4;  
    void printPrivateVar() {  
        try {  
            System.out.println(A.class.getDeclaredField("privateN4") + ": " + this.privateN4);  
        } catch (NoSuchFieldException e) {  
            throw new RuntimeException(e);  
        }  
    }  
}

public class B extends A {  
}

public class Main {  
    public static void main(String[] args) {  
        B b = new B();  
        b.printPrivateVar();  
    }  
}

console output:
private int A.privateN4: 4
```