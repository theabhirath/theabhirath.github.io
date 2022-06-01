---
title: A brief introduction to the Imperative Programming Paradigm
tags:
    - programming
---

When learning to code for the first time, it can be overwhelming to see terms like **functional** or **object-oriented** be thrown around by more experienced programmers. In this series of articles, I wanted to give a brief overview of what these paradigms actually mean, and demonstrate some very small programs implementing some of these. These articles are not meant to be comprehensive in any fashion, although I do go over the most common paradigms and try to give you a sense of what they mean.

In this article, I go over what a programming paradigm is and specifically dive into the **imperative programming paradigm**. Let’s dive right in!

---

What is a **programming paradigm?**

Simply put, it is a way to classify programming languages based on their features. Some paradigms deal with the **execution model**, the way in which each line of code is executed. Others are concerned with organisation, such as grouping code into specific units.

There are many types of programming paradigms for classifying programs using various criteria, but there are a few things to keep in mind:

1. While there is a broad agreement over how these paradigms work and which languages come under which, many of the specifics are hotly debated over. In reality, these paradigms are idealisations that are seldom achieved — most programming languages are built on multiple paradigms working together.
2. You may see several heated debates over some paradigms being better than others on the internet. But it is important to remember that which paradigm you use while designing a program depends on what you want to accomplish with it, and how comfortable you yourself are with the paradigm in question.

---

Any computer program stores data in variables, which represent storage locations in a computer’s memory. The contents of these memory locations, at any given point in the program’s execution, is called the program’s **state**.

_Imperative Programming_ is a paradigm in which programs are composed of **statements** that change a program’s state. An imperative program consists of commands for the computer to perform. Imperative programming focuses on describing _how_ a program operates.

The most popular programming languages are all imperative, and the rationale behind this is that the implementation of computer hardware itself is in an imperative fashion. Both machine code and assembly are written in an imperative style, where the program state is described by the contents of memory and the statements carry out various operations on these contents.

Here too, two sub-paradigms exist: **procedural** and **object-oriented** programming.

## Procedural programming

Procedural programming is a subset of the imperative paradigm in which the program is built from one or more **procedures**, also called **subroutines** or **functions.** A subroutine is simply a sequence of program instructions that performs a specific task, packaged as a unit. This unit can then be used in programs wherever that particular task should be performed.

```c
#include <stdio.h>

int add(int a, int b){
  return a + b;
}

int main(void){
  int x = 1;
  int y = 2; 
  int sum = add(x, y);
  printf("%d\n", sum);
  return 0;
}
```
<center><i>A simple C program to return the sum of two numbers via a procedure <code>add</code> that takes two arguments.</i></center>

<br>

The above program is an example of the implementation of the procedural paradigm. A procedure was used to add the two numbers, and the return value was assigned to a new variable. Each line of the program represents a change in the state of the program, as you will realise on careful reading.

## Object-Oriented Programming (OOP)

The most popular programming paradigm in software engineering. It relies on **objects:** which are abstract, custom structures that contain both data **fields** (also referred to as **attributes** or **properties**)**,** for storing information, and **methods,** which are procedures that are specific to an object that can be used to modify or access it. In most commonly-used languages, this is associated with **classes,** which are blueprints for creating an _instance_ of an object.

That seems very technical. So let’s deal with an example. A class is an example of an object such as a car. And instances are specific cars, like that old piece of junk that your family refuses to throw or the brand new Jeep the neighbour purchased.

> This is a very superficial example, obviously. Even in cars, there's passenger vehicles and sports vehicles; F1 cars, SUVs, sedans and hatchbacks are all cars and do in fact correspond to a "blueprint" for a car. So the more exact example would be of an abstract class named `Car` , which is subclassed by several other abstract classes like `FormulaOne`, `Sedan`, which are then further subclassed by concrete classes like `MercedesSClass` or `HondaCivic`, which finally have instances that people can purchase. And that's just a very simple example. There's obviously tons of more design choices that can be made along the way resulting in a very different hierarchy, but that's the gist of it.

The OOP paradigm has a lot of distinguishing features, but I'm gonna go through some of the widely used ones:

### Message Passing

Message passing is a technique for invoking behaviour (i.e., running a program) on a computer. In contrast to the traditional technique of calling a program by name, message passing uses an object model to distinguish the general function from the specific implementations. The invoking program sends a message and relies on the object to select and execute the appropriate code.

Now, that sounds like a lot of words, but it really isn’t very complicated. All it wants to say is that instead of one program containing all the functions that we need for a sophisticated system to work, an intermediate program is designed to pass _messages_ — or in other words, information regarding _what_ functions are to be called with what parameters— to objects that have been implemented in other programs. The key idea here is that the intermediate program needs to have no knowledge whatsoever of how the main function is being implemented — it relies on the _object_ to execute that code successfully and return the answer.

Considered to be among the most vital features for the object-oriented paradigm, message passing is used _everywhere_ in modern software. It is among the many features used that allow computers to interact via networks such as the Internet.

### Encapsulation

Encapsulation is a concept where data and the methods that manipulate the data are bound together into a class. This lends itself to _information hiding,_ which is of critical importance in many fields. In languages such as Java, classes can explicitly enforce restrictions by using the keywords `private`, `public` and `protected`. In some other languages, this is not enforced strictly but rather as a convention (such as using names that begin with an underscore for private methods or variables in Python).

Encapsulation is the guiding principle behind a class **interface.** The interface is what any code outside of the class sees the class as; thus, private variables and methods are hidden, and specific methods are implemented to control access (**getters** or **accessors**) and modification (**setters** or **mutators**). An interface is particularly useful as a way to abstract away a lot of the code behind the scenes and deal with a “black box” where we are only concerned with the specific outputs that we get for specific inputs.

An interesting example to illustrate the concept of encapsulation would be a television set from the ’90s. The particular model of the television in front of you is an _instance_ of a more general _class_ of televisions; the buttons that one can press on the front of the screen are the *methods* that compose the interface. The screen shows you _visual data_ that is also associated with the interface; and finally, the processes that run behind the screen which cannot be seen by you are akin to _private_ methods.

One final use of encapsulation before we move on: it allows programmers to group all code related to a certain set of data in one single class, making organisation easier and resulting in better comprehension when read by other programmers.

### Inheritance

Inheritance is a concept where classes can be organised into a hierarchy. This is best demonstrated by an example — a class `Lizard` may _inherit_ both data and methods from a class `Reptile,` since a lizard is a “subclass” of a reptile.

Inheritance also allows you to add new variables or methods to subclasses — for example, an `Employee` class that derives from a `Person` class will inherit the `first_name` and `last_name` attributes (as well as a method `get_full_name` that returns the full name of the person), but will also probably define new variables `position` and `salary` for an accurate representation. This allows programmers to mirror real-world relationships as code objects very easily and intuitively.

Where inheritance truly reveals its power is in the ability to be able to override methods from the ‘superclass’ for specific subclasses (for example, in an `Ostrich` class that inherits from a `Bird` class, you might want to override the `Flight` method so as to prevent people from questioning your knowledge of zoology).

Another extremely useful feature of inheritance is to allow the creation of **abstract classes**, which are classes that cannot be directly instantiated to form objects. Instead, other **concrete classes** that _can_ be instantiated to give objects inherit from them.

```python
class Animal:  
    def speak(self):  
        print("Animal Speaking")  

class Dog(Animal) :  
    def bark(self):  
        print("dog barking")  
d = Dog()  
d.bark() # prints "dog barking"  
d.speak() # prints "Animal Speaking"
```

<center><i>An example of single inheritance in Python. The method speak was never explicitly defined for the class <code>Dog</code>, but it inherited it from the superclass <code>Animal</code>.</i></center>

<br>

The implementation of inheritance varies across languages — some allow only for **single inheritance**, i.e. a class can have only one superclass. Others allow for limited multiple inheritance; and some, like Go, do not allow inheritance at all.

### Polymorphism

Polymorphism can be used to refer to several different ideas that are closely related, but the two ideas that objects use most often are **function** or **operator overloading,** and **subtyping.**

In function overloading, the same method behaves differently when applied to different arguments based on their _type_. The most commonly used example for this is addition behaving differently for different arguments, such as the following use-cases:

1. `1 + 2 = 3`
2. `3.14 + 0.0015 = 3.1415`
3. `1 + 3.7 = 4.7`
4. `[1, 2, 3] + [4, 5, 6] = [1, 2, 3, 4, 5, 6]`
5. `[true, false] + [false, true] = [true, false, false, true]`
6. `"bab" + "oon" = "baboon"`

To handle these six function calls, four different pieces of code are needed

- In the first case, integer addition must be invoked.
- In the second and third cases, floating-point addition must be invoked (with implicit type casting in the third case).
- In the fourth and fifth cases, list concatenation must be invoked.
- In the last case, string concatenation must be invoked.

This can be achieved via implementing the addition function as a method separately for each type: integer, floating-point, list and string — and defining them to have different meanings based on the type of the example passed.

Another example of polymorphism is via subtyping, where programming languages allow a function that takes an argument of a particular type to work correctly even if a _subtype_ (in OOP, this would mean an object of a subclass of the original class) is passed to it.

```java
abstract class Animal {
    abstract String talk();
}

class Cat extends Animal {
    String talk() {
        return "Meow!";
    }
}

class Dog extends Animal {
    String talk() {
        return "Woof!";
    }
}

static void letsHear(final Animal a) {
    println(a.talk());
}

static void main(String[] args) {
    letsHear(new Cat());
    letsHear(new Dog());
}
```

<center><i>An example of both types of polymorphism in Java. Function overloading has been used with the function <code>talk</code>, while subtyping has been used with <code>letsHear</code>.</i></center>

<br>

The choice of which version of a method to call may be based either on a single object, or on a combination of objects. In most languages such as C++, Java and Python, the method is called based on a single object and is called **single dispatch.** For example, consider the code:

```md
dividend.divide(divisor)
```

Building on an earlier concept, this can be thought of as _sending a message_ named `divide` with a parameter `divisor` to the object `dividend`. The version of the function division that has to be implemented depends only on the type of the _dividend_, since the method being called belongs to the class that `dividend` is an object of (we inferred this from the **dot** notation, which is used to access any methods/variables that belong to an object).

A more powerful method of polymorphism called **multiple dispatch** is used in languages such as Common Lisp and Julia. The implementation of polymorphism in those cases is _not_ object-based. This just leads me to tell you that all the features of OOP that we have covered here are not exclusive to OOP, nor are they all present in the same form (or at all) in different languages’ implementation of OOP. But these are definitely among the more popular features of which I have attempted to give you an overview without delving too deep into the rabbit hole. This leads me to one final feature…

### Open Recursion

This is the ability for one method to invoke another method of the same object via a special variable called `self` (Python) or, in some languages, `this` (Java). The special behaviour of `self` is that it is _late-bound._ In late binding, the method being called upon an object is looked up by name at runtime. In other words, a name is associated with a particular operation or object at runtime, rather than during compilation. This allows a method defined in one class to invoke another method that is defined later.

Whew! That’s a lot of words. So what do I want to say over here?

Well, when you write functions outside of an object i.e. not as a method, but as a subroutine — then one of the major challenges that you might face is when you have a bunch of functions that all somehow refer to each other. Say there is a function `f1` that calls `f2` and `f3`, `f2` itself calls `f3` and `f3` calls `f1`.

Well, if you try to write this out in linear fashion outside of an object, in any possible order of functions, you will face a problem. And that problem is that no matter which order you choose, one of the functions getting called will not have been defined when it is called. And the program will be _very_ upset with you.

So what is the solution? _Open recursion_. The recursion here isn’t literal — well, you _could_ theoretically write three functions as I’ve mentioned above, but it isn’t exactly the most common use case. But there _are_ instances in which you want all the functions defined in one block to be able to _see_ each other, if you will, and therefore be able to call each other as well. This is what open recursion allows you to do.

---

# Conclusion

If you’d made it this far, I’d like to thank you for continuing to read through till the end. It’s readers like you who inspire me to write. 

In the next article, I will be talking about function evaluation strategies, before we return to talk about declarative programming. Until next time!

---

_Thanks for reading! I hope you’ve enjoyed reading this article. You can find me on_ [_Linkedin_](https://www.linkedin.com/in/theabhirathanand/)_,_ [_Twitter_](https://twitter.com/theabhirath) _and_ [_GitHub_](http://github.com/theabhirath).