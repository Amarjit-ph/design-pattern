# Design pattern



# What is a Design Pattern?
A design pattern is a proven, reusable solution to a common problem in software design. Think of it as a blueprint or template that helps developers solve challenges efficiently without reinventing the wheel. Design patterns promote code reusability, scalability, and maintainability, and they offer a shared language for developers to communicate ideas clearly.

# What does a Design Pattern consist of?
A design pattern typically consists of three key elements: the problem, the solution, and the consequences. It describes the context in which the pattern applies, outlines the structure and interaction of classes or objects involved, and discusses the trade-offs and impact of applying the pattern. Essentially, it defines when, why, and how to use a particular approach to solve recurring software design challenges.

Key Elements of a Design Pattern:

1. Pattern Name - A meaningful name to identify and communicate the pattern easily.
2. Problem - The specific design issue or scenario the pattern addresses.
3. Solution - The core design structure, relationships, and guidelines to solve the problem.
4. Participants - The classes, objects, or methods involved in implementing the pattern.
5. Consequences - The benefits, limitations, and trade-offs of applying the pattern.

Simple Example: Singleton Pattern

- Pattern Name: Singleton
- Problem: Ensure only one instance of a class exists and provide a global point of access.
- Solution: Private constructor + static method returning the single instance.
- Participants: Singleton class, static instance variable, static accessor method.
- Consequences: Controlled access, but can be hard to test (tight coupling).

# History of Design Patterns
The concept of design patterns originated in architecture, introduced by Christopher Alexander in the 1970s to describe solutions to recurring building design problems. Later, in 1994, four software engineers—Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides (known as the Gang of Four or GoF)—adapted this idea to software development. Their book, "Design Patterns: Elements of Reusable Object-Oriented Software," formalized 23 foundational patterns that are still widely used today.

# Why Should You Learn Design Patterns?
Learning design patterns helps you write cleaner, more efficient, and maintainable code. Patterns provide time-tested solutions to common problems, saving you from reinventing the wheel. They also improve communication among developers by offering a shared vocabulary, making it easier to understand and collaborate on complex systems. Ultimately, mastering patterns makes you a better problem solver and a more adaptable developer.

Key Benefits:

- Reusable Solutions - Apply proven strategies to recurring design challenges.
- Clean & Maintainable Code - Promotes structured, modular, and scalable code.
- Better Communication - Speak the common language of design patterns in team discussions.
- Improved Problem-Solving - Quickly recognize and apply appropriate solutions.

# Classification of Design Patterns
Design patterns are categorized based on the type of problem they solve in software design. They are mainly divided into Creational, Structural, and Behavioral patterns. Each category addresses different aspects of object creation, structure, or interaction, making it easier to choose the right pattern for a specific need.

Key Categories:
1. **Creational Patterns** - Focus on how objects are created, ensuring flexibility and control over object creation.
2. **Structural Patterns** - Deal with how classes and objects are composed to form larger structures.
3. **Behavioral Patterns** - Focus on communication and responsibility between objects.

# Creational Design Patterns
Creational design patterns focus on object creation mechanisms, providing flexibility and efficiency in creating objects. Instead of instantiating objects directly, these patterns offer ways to create objects while hiding the creation logic. This leads to better scalability, easier maintenance, and loose coupling between classes.

Key Patterns:
1. **Singleton Pattern**
Ensures only one instance of a class exists and provides a global access point.

    Example: Database connection manager.

2. **Factory Method Pattern**
Defines an interface for creating objects but lets subclasses decide which class to instantiate.
    Example: ShapeFactory that returns Circle, Square, etc., based on input.

3. **Abstract Factory Pattern**
Provides an interface for creating families of related objects without specifying their concrete classes.
    Example: UI Toolkit factory producing different themes (Light, Dark).

4. **Builder Pattern**
Separates the construction of a complex object from its representation, allowing the same construction process to create different representations.
    Example: Building a complex Meal object step by step.

5. **Prototype Pattern**
Creates new objects by copying an existing object (prototype) instead of creating from scratch.
    Example: Cloning game characters or settings.

# Structural design patterns
Structural design patterns focus on how classes and objects are composed to form larger, more flexible structures. They help ensure that if one part of a system changes, the entire structure doesn’t have to change. These patterns promote efficient and scalable relationships between entities while keeping them loosely coupled.

Key Patterns:
1. **Adapter Pattern** - Converts one interface into another that a client expects, allowing incompatible interfaces to work together.

    Example: Power socket adapter converting different plug shapes.

2. **Bridge Pattern** - Separates abstraction from implementation so that both can vary independently.
    
    Example: Remote control (abstraction) working with different devices like TV or Radio (implementation).

3. **Composite Pattern** - Composes objects into tree structures to represent part-whole hierarchies, allowing clients to treat individual objects and compositions uniformly.
    
    Example: File system with folders containing files or other folders.

4. **Decorator Pattern** -Adds new functionality to an object dynamically without altering its structure.
    
    Example: Adding scrollbars or borders to a window in a GUI.

5. **Facade Pattern** - Provides a simplified interface to a complex subsystem, making it easier to use.
    
    Example: A hotel booking system that combines room booking, payment, and notifications under one interface.

6. **Flyweight Pattern** - Reduces memory usage by sharing as much data as possible with similar objects.
    
    Example: Rendering large numbers of similar objects in a game (like trees).

7. **Proxy Pattern** - Provides a placeholder or surrogate to control access to another object.
    
    Example: Virtual proxy loading an image only when it is needed.

# Behavioral design patterns
Behavioral design patterns focus on communication between objects, defining how objects interact, distribute responsibilities, and manage the flow of information. These patterns help ensure loose coupling while promoting flexibility and reusability of behavior.

Key Patterns:
1. **Observer Pattern** - Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

    Example: Notification system where multiple users are notified when new content is published.

2. **Strategy Pattern**
Defines a family of algorithms, encapsulates each one, and makes them interchangeable at runtime.
    
    Example: Different payment methods (Credit Card, PayPal, UPI) selected at checkout.

3. **Command Pattern**
Encapsulates a request as an object, allowing parameterization of clients with different requests and queuing or logging of requests.
    
    Example: Remote control commands like turning a device on or off.

4. **Chain of Responsibility Pattern**
Passes a request along a chain of handlers, where each handler decides either to process the request or pass it to the next handler.
    
    Example: Customer support ticket escalation (Level 1 → Level 2 → Manager).

5. **Mediator Pattern**
Defines an object that centralizes complex communication and control logic between objects.

    Example: Chatroom where users send messages via a central mediator.

6. **Template Method Pattern**
Defines the skeleton of an algorithm in a method, deferring some steps to subclasses without changing the algorithm's structure.
    
    Example: A generic data processing algorithm where specific steps (like parsing) can vary.

7. **Iterator Pattern**
Provides a way to access elements of a collection sequentially without exposing the underlying representation.
    
    Example: Looping through a list or array using an iterator.

8. **State Pattern**
Allows an object to alter its behavior when its internal state changes, appearing as if its class changed.
    
    Example: Traffic light changing behavior based on its current state (Red, Green, Yellow).

9. **Visitor Pattern**
Lets you add further operations to objects without modifying them, by defining a new visitor class.
    
    Example: Adding new functionalities like exporting data in various formats without altering the data classes.

10. **Memento Pattern**
Captures and restores an object's internal state without violating encapsulation.
    
    Example: Undo/Redo functionality in text editors.