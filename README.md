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

## What is a Service?
A service class is responsible for implementing of usecase. for example in the above sample of the order processing system we should create a service to implement place order usecase, etc.
The service class is a stateless singleton, and that is by design. It is supposed to be a thin layer that orchestrates the business.

## What is a Repository?
"Mediates between the domain and data mapping layers using a collection-like interface for accessing domain objects" (Martin Fowler).
Repositories, in practice, are used to perform database operations for domain objects (see Entities). Generally, a separate repository is used for each aggregate root or entity.
the repository pattern have two purposes; first it is an abstraction of the data layer and second it is a way of centralising the handling of the domain objects.

The Repository Pattern is a design pattern commonly used in software development to manage the interaction between the application and the data storage layer (such as a database). It provides a structured way to organize data access logic, encapsulating database queries and operations within a separate layer called a "repository." This pattern is often used to promote separation of concerns, making the data access code more maintainable and testable.

Key Concepts of the Repository Pattern:
Separation of Concerns:

The repository acts as an intermediary between the application logic (business logic layer) and the data access logic. Instead of writing database queries directly in the service layer or business logic, they are abstracted and managed inside repository classes.
Encapsulation of Data Access Logic:

All the database operations (like CRUD operations — Create, Read, Update, Delete) are encapsulated inside the repository. This keeps the business logic free of database-specific details, leading to cleaner and more maintainable code.
Abstraction:

The repository provides a layer of abstraction between the domain models (or entities) and the database. The application interacts with the repository without needing to know about how data is stored or retrieved (e.g., SQL, NoSQL, or in-memory data). The repository usually works with domain entities or aggregate roots, allowing data to be treated as objects.
Testability:

Because the repository isolates the data access logic, it becomes easier to test the application logic without having to depend on the actual database. You can mock the repository and test the business logic in isolation.
Single Responsibility Principle:

Each repository is responsible for handling a specific entity (like CustomerRepository or OrderRepository), which makes the design modular and adheres to the Single Responsibility Principle of SOLID design.

## What is a Generic Repository?
It provides a generalized and reusable way to handle data persistence operations (CRUD - Create, Read, Update, Delete) for different types of entities without having to write redundant code for each specific entity.
### Benefits:
Code Reusability: You can avoid writing repetitive data access logic for each entity.
Single Responsibility: The generic repository handles CRUD operations, while business logic is kept separate.
Easier Testing: It simplifies mocking repositories for unit testing because it provides a common interface.
### Potential Downsides:
Over-Generalization: In some cases, you may need entity-specific operations that don't fit well in a generic structure, requiring additional layers or patterns.
Complexity: It can introduce more complexity in small projects, where a simple repository pattern for each entity might be enough.

## What is a DTO?
A DTO is used to transfer data between different layers of an application (e.g., between the service layer and the presentation layer or between client and server in web APIs).
It is a simple object, usually containing just data with no business logic. Its primary purpose is to carry data from one system to another.

## What is a View Model?
A ViewModel is specific to the UI layer and is designed to represent the data that is needed to render a particular view.
It often combines data from multiple sources, processes it, or transforms it in ways that make it easier for the view (UI) to consume. It can also contain UI-specific logic or formatting.

## What is a Unit Of Work?


