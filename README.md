# Idioms and Concepts
I will describe some idioms and concepts of programming
Programmers always use some words that may not know the key meaning of all of them. In this repo, I describe some of them with examples from the Asp.net core.

## What is a design pattern?
Design patterns are binaries of problem or problem and solution, generally with useful recommendations for assigning responsibilities to objects.

## What are GRASP patterns? (General Responsibility Assignment Software Patterns)
Some patterns have a series of principles for designing objects and assigning responsibilities to them.
Grasp patterns are:
• Information Expert
• Creator
• High Cohesion
• Low Coupling
• Controller

### Problem: Who is responsible for handling the events of a system?
Solution: We assign the responsibility of receiving and handling system events to a class with the following definitions:
1- It is the indicator of the whole system, that is, for the whole system or subsystem
2- Expressing a use case means we define a controller for each use case.

## What is a Controller?
Controller is a non-user class that is responsible for receiving and handling system events.
The controller does not do anything on the event, it just redirects it to another object

how do detect and create controllers?
one way is to create a controller per use-case.

### what is the use-case?
A use-case is the interaction of the user with the system. For example: in an order-processing system placing an order is a use-case

![image](https://github.com/user-attachments/assets/1488adf2-62cd-402a-8952-abd7adf744e7)

The Use-Case Controller pattern deals with the problem of mapping use-case specifications to a cost-effective implementation easily maintainable. The
pattern suggests delegating the responsibility for managing a use-case's flow of execution to a specialized controller object, thus localizing this functionality
and its possible changes. Use-case controllers provide a uniform way of coordinating actor events, user interfaces, and system services. Additionally,
use-case controllers increment the potential variability of use cases, either by enabling the plug-in of use-case extensions and inclusions or by replacement
of user interface components and system components.

![image](https://github.com/user-attachments/assets/6326806b-a4e2-4fef-a140-ddae4d3498e1)


![image](https://github.com/user-attachments/assets/ada16d8c-90e2-4c85-94c2-cf50291f6515)


For each one of the use cases above create a use-case controller class. Although being possible, and sometimes convenient, to
create a use-case controller class for each use-case candidate, this decision must be made by the developer after refinement of
the use-case participant classes and, thus, knowing well the events exchanged between them. At this stage, it can be decided
to assign one, two or more use-case controllers to a single use-case, or even none. Typically, a use-case controller class
includes methods to start and finish its execution, to invoke specific use-case actions, and to fire events to interface objects
and entity objects.



