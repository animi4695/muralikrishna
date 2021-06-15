---
title: "OOP for Interviews"
date: 2020-06-12T01:12:26+05:30
draft: false
images:
tags: [interviews, system design, coding]
---
> The goal of this article is to serve as a quick reference of some of the OOP concepts right before Interviews. Although this article is more inclined towards C# language, the concepts are language agnostic.

#### Object Oriented Programming:
Object-Oriented Programming refers to the programming paradigm defined using objects instead of just functions and methods like in a procedural Programming. Objects can be considered as real world instances of entities like class, that have attributes and methods.

#### Features of OOP:
* **Inheritance**:
  : It is a mechanism by which an object or class (referred to as a child) is created using the definition of another object or class (referred to as parent).
- **Polymorphism**:
  : It means "Many Forms". It is the ability of an object to take different forms and thus depending upon the context, to respond to same message in different ways.   
Eg: In a Chess game, a chess piece can take many forms like kind, bishop, pawn etc. All these pieces will respond differently to the "move" message/function call. 
*2 Types of Polymorphism:*
   * **Compile-Time** (static/early binding) : 
   ```
   class CompileTimePolymorphism {
       // 1st method
       int add(int x, int y) {
           return x+y;
        }
        // 2nd method
        int add(int x, int y, int x) {
            return x+y+z;
        }
    }
    
    class Test {
        CompileTimePolymorphism demo = new CompileTimePolymorphism();
        // the Compiler looks at the argument types and decides to call method 1
        Console.WriteLine(demo.add(2,3));
        // the Compiler looks at the argument types and decides to call method 2
        Console.WriteLine(demo.add(2,3,4));
    }
   ```
   * **Run-Time** (Dynamic/Late Binding) :
   ```
    class AnyVehicle{ 
        public void move() { 
            Console.WriteLine("Any vehicle should move!!"); 
        } 
    } 
    class Bike: AnyVehicle { 
        public void move(){ 
            Console.WriteLine("Bike can move too!!"); 
        } 
    } 
    class Test{ 
        public static void main(String[] args) { 
            AnyVehicle vehicle = new Bike(); 
            vehicle = new AnyVehicle(); 
            vehicle.move(); 
        } 
    }
   ```
- **Encapsulation**:
  : It is the mechanism of binding the data together and hiding it from outside world. It is achieved when objects keeps its state private so that other objects don't have access to its state. Instead they can access this state only through a set of public functions.   

- **Abstraction**:
  : It can be thought of as a natural extension of Encapsulation. In a large system, objects talk to each other, which makes it difficult to maintain a large codebase. Abstraction helps in hiding internal implementation details of objects and only revealing operations that are relevant to other objects. This is achieved with the help of abstract methods/classes.   
  Eg. Consider a car, you only need to know how to run a car, and not how the wires are connected inside it. Similarly you can map this to a programming scenario while answering the question.  

**Class**:
: Template or Blueprint, which contains some attributes, properties and functions. When an object is created, it automatically takes the data and functions defined in the class.

**Object**:
: refers to the instance of class. It contains the instances of members and functions defined in the class template. Objects consume memory space when they are initialized.

**Constructor**:
: Special methods whose name is same as class name, they help to initialize the objects. If there is no constructor written, the compiler automatically creates a default constructor.

**Interface**:
: special type of class which contains methods but no definition. Only declaration of methods, properties is allowed inside interface. They are are used for loose coupling, extensibility and implementation hiding.

**Abstract Classes**:
 - An abstract class is a special kind of class that can not be instantiated. 
 - An abstract class is only to be sub-classed (inherited from). In other words, it only allows other classes to inherit from it but can not be instantiated. Advantage is that it enforces certain hierarchies for all the sub classes.
 - An abstract class can never be sealed or static but abstract class can have static methods. 
 - An abstract member cannot be static or private or virtual.
 - An abstract class can have abstract as well as non abstract methods.
 - Abstract members can only be declared inside an abstract class.
 - A concrete class cannot inherit more than one abstract class. (multiple inheritance is not possible) (C#)   
 "Abstract class is used when your base class should provide the default implementation of certain methods whereas other methods should be open to being overridden by child classes that time you have to use abstract classes."

 > NOTE: This article is a WIP. I'll try to add small pieces of more concepts in the near future.



