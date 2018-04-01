# Singleton Pattern

**Zhenguo Chen**

## Introduction
As described in [wiki](https://en.wikipedia.org/wiki/Singleton_pattern):

>In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of
a class to one object. This is useful when exactly one object is needed to coordinate actions across the system.
The concept is sometimes generalized to systems that operate more efficiently when only one object exists, or 
that restrict the instantiation to a certain number of objects. The term comes from the mathematical concept of
a singleton.

The singleton pattern is known because it restricts instantiation of a class to a single object. Usually, people 
implement singleton by creating a class with a method that creates a new instance of the class if one doesn't 
exist. If an instance already exists, it will simply return a reference to that object.

## Why Singleton

You may ask why people want to use singleton. Suppose we have to use a single object of a class throughout our 
whole application. For instance, we want to control access to resources such as database connections or sockets,
and we only allow one connection for our database. How are you going to do that?

One possible solution is to declare a global object, and use this single object everywhere in our program. 
However, this is against our fundamental principles of object orientation, such as data encapsulation. Also, 
some programming languages like Java do not support global variables or functions.

Another possible solution is to use `static` class. A static class is loaded when the execution of a program starts,
and we don't need initialize an instance to use the static methods. It would be useful when you want to collect
related pieces of functionality without maintaining any internal state in any object. For instance, the Math 
class in Java, which contains a bunch of related functions that can be used outside the context of any specific
object instance. However, when you do want to have an actual object, and you want to restrict the instantiation,
static class may not be a good choice.

Therefore, when we want to create only one instance of a class throughout the lifetime of our application, 
singleton pattern can be helpful. The singleton class is instantiated at the time of first access and same 
instance is used thereafter. It can be easily implemented in any object oriented programming languages like C++,
Java and C#. In next section, I will show you how to implement a singleton in C++. Here is also an 
[implementation](https://addyosmani.com/resources/essentialjsdesignpatterns/book/) in JavaScript.

## Implementation

In the program below, I implemented a Singleton class using `private constructor`. By using private constructor,
we can restrict the instantiation of this class and always use the same object. By invoking the static function
`getInstance()`， we can get a reference to the single object of our Singleton class.

```c++
class Singleton{
private:
    static Singleton *obj;
    // private constructor
    Singleton(){

    }
public:
    int x = 1;
    static Singleton* getInstance(){
        if(obj == NULL)
            obj = new Singleton();
        return obj;
    }
};

// initializing Singleton's static data member
Singleton *Singleton::obj = 0;
```

In `main` function, we can use this object as below. When `getInstance()` function is invoked for the first time,
a new object will be instantiated and returned. Then, the same object will be returned every time `getInstance()`
is used thereafter, which means only one single object of this Singleton class will be created and used.

```c++
int main(){
    cout<< Singleton::getInstance()->x << endl; // output 1
    return 0;
}
```

Reference:
* [Singleton Pattern](https://en.wikipedia.org/wiki/Singleton_pattern)
* [Singleton Pattern & its implementation with C++](https://www.codeproject.com/Articles/1921/Singleton-Pattern-its-implementation-with-C)
* [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#singletonpatternjavascript)
