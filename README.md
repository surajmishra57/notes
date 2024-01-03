# notes
This is only for leaning purpose with example of topics 

# Method Refrence In Java : 

Method references in Java provide a shorthand notation to refer to methods using the double colon (::) syntax. They allow you to treat a method as a lambda expression.

There are four main types of method references:

1. Static Method Reference:
// Lambda expression
MyFunctionalInterface myFunc = (s) -> MyClass.staticMethod(s);

// Method reference
MyFunctionalInterface myFunc = MyClass::staticMethod;

2. Instance Method Reference of a Particular Object:
// Lambda expression
SomeClass someObject = new SomeClass();
MyFunctionalInterface myFunc = (s) -> someObject.instanceMethod(s);

// Method reference
SomeClass someObject = new SomeClass();
MyFunctionalInterface myFunc = someObject::instanceMethod;

3. Instance Method Reference of an Arbitrary Object of a Particular Type:
// Lambda expression
MyFunctionalInterface myFunc = (s) -> s.length();

// Method reference
MyFunctionalInterface myFunc = String::length;

4. Constructor Reference:
// Lambda expression
MyInterface myInterface = () -> new MyClass();

// Constructor reference
MyInterface myInterface = MyClass::new;

In the examples above, MyFunctionalInterface and MyInterface represent functional interfaces with a single method.

Here's a simple example of a functional interface and using method references:

@FunctionalInterface
interface MyFunctionalInterface {
    void myMethod(String s);
}

class MyClass {
    static void staticMethod(String s) {
        System.out.println("Static method: " + s);
    }
}

public class MethodReferenceExample {
    public static void main(String[] args) {
        // Using a static method reference
        MyFunctionalInterface staticRef = MyClass::staticMethod;
        staticRef.myMethod("Hello");

        // Using an instance method reference of a particular object
        SomeClass someObject = new SomeClass();
        MyFunctionalInterface instanceRef = someObject::instanceMethod;
        instanceRef.myMethod("World");
    }
}

In this example, MyFunctionalInterface is a functional interface with a single method myMethod. The staticMethod of MyClass is used as a static method reference, and the instanceMethod of an instance of SomeClass is used as an instance method reference.
