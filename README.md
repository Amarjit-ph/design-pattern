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

## 1. Singleton Pattern 
The Singleton Pattern ensures that a class has only one instance throughout the application and provides a global access point to that instance. It is useful when exactly one object is needed to coordinate actions across the system, like configuration settings or database connections.

Key Features:
- Ensures only one instance of a class exists.
- Provides global access to that instance.
- Controls concurrent access in multithreaded scenarios (if needed).

```js
class Database {
  constructor() {
    if (Database.instance) {
      return Database.instance;
    }
    console.log("Creating new Database connection...");
    Database.instance = this;
  }

  connect() {
    console.log("Connected to Database.");
  }
}

// Usage
const db1 = new Database();
db1.connect(); // Output: Creating new Database connection... Connected to Database.

const db2 = new Database();
db2.connect(); // Output: Connected to Database.

console.log(db1 === db2); // Output: true
```

Ensures that only one instance of a class exists and provides a global access point.

🔹 Use Cases:

1. Database Connection Pool – Ensures a single database connection is reused.
2. Logging System – Centralized logging to maintain consistency across the app.
3. Configuration Manager – Loads app settings once and provides a global reference.
4. Thread Pool – Manages a single set of threads shared across multiple tasks.





## 2. Factory Method Pattern
The Factory Method Pattern provides an interface for creating objects but allows subclasses to decide which specific class to instantiate. Instead of calling a constructor directly, the creation logic is handled in a method, promoting flexibility, loose coupling, and easier code maintenance.

Key Features:
- Defines a common interface for object creation.
- Delegates the instantiation to subclasses.
- Promotes code flexibility by decoupling object creation from usage.

```js
// Shape interface
class Shape {
  draw() {}
}

// Concrete classes
class Circle extends Shape {
  draw() { console.log("Drawing Circle"); }
}

class Square extends Shape {
  draw() { console.log("Drawing Square"); }
}

// Factory Method
class ShapeFactory {
  static getShape(type) {
    if (type === "Circle") return new Circle();
    if (type === "Square") return new Square();
    return null;
  }
}

// Usage
const shape1 = ShapeFactory.getShape("Circle");
shape1.draw(); // Output: Drawing Circle

const shape2 = ShapeFactory.getShape("Square");
shape2.draw(); // Output: Drawing Square
```

Creates objects without specifying the exact class, allowing subclasses to determine the object type.

🔹 Use Cases:

1. Shape Factory (Circle, Square, etc.) – Returns shape objects based on input.
2. Notification System (Email, SMS, Push) – Creates a notification object based on the required type.
3. Vehicle Factory (Car, Bike, Truck) – Instantiates different vehicles dynamically.
4. Parser Factory (XML, JSON, CSV) – Creates the correct parser based on file format.


## 3.  Abstract Factory Pattern
The Abstract Factory Pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes. It allows you to produce multiple types of related objects that share a common theme, ensuring consistency across products while keeping creation logic flexible and scalable.

Key Features:
- Produces families of related objects.
- Promotes consistency without tight coupling.
- Allows easy swapping of product families (e.g., themes, platforms).

```js
// Abstract products
class Button {
  render() {}
}

class Checkbox {
  render() {}
}

// Concrete products for Light theme
class LightButton extends Button {
  render() { console.log("Rendering Light Button"); }
}

class LightCheckbox extends Checkbox {
  render() { console.log("Rendering Light Checkbox"); }
}

// Concrete products for Dark theme
class DarkButton extends Button {
  render() { console.log("Rendering Dark Button"); }
}

class DarkCheckbox extends Checkbox {
  render() { console.log("Rendering Dark Checkbox"); }
}

// Abstract Factory
class UIFactory {
  createButton() {}
  createCheckbox() {}
}

// Concrete Factory: Light Theme
class LightFactory extends UIFactory {
  createButton() { return new LightButton(); }
  createCheckbox() { return new LightCheckbox(); }
}

// Concrete Factory: Dark Theme
class DarkFactory extends UIFactory {
  createButton() { return new DarkButton(); }
  createCheckbox() { return new DarkCheckbox(); }
}

// Usage
function renderUI(factory) {
  const button = factory.createButton();
  const checkbox = factory.createCheckbox();
  button.render();
  checkbox.render();
}

const lightTheme = new LightFactory();
renderUI(lightTheme); // Output: Rendering Light Button, Rendering Light Checkbox

const darkTheme = new DarkFactory();
renderUI(darkTheme); // Output: Rendering Dark Button, Rendering Dark Checkbox
```

Creates families of related objects without specifying their concrete classes.

🔹 Use Cases:

1. UI Toolkit (Light & Dark Themes) – Generates buttons, text boxes, and checkboxes based on the theme.
2. Cross-Platform Development (Windows, macOS, Linux) – Creates UI components compatible with different operating systems.
3. Game Development (2D & 3D Engines) – Abstracts game objects based on rendering type.
4. Database Driver Factory (MySQL, PostgreSQL, MongoDB) – Provides database connections dynamically.


## 4. Builder Pattern

The Builder Pattern is used to construct complex objects step by step, allowing you to create different representations of the same object. It separates the construction process from the final object representation, making the code cleaner and more manageable, especially when dealing with objects with many optional parameters.

Key Features:
- Builds complex objects step by step.
- Allows varying internal representations.
- Improves readability and manageability of object creation.

```js
// Product
class Meal {
  constructor() {
    this.items = [];
  }
  addItem(item) {
    this.items.push(item);
  }
  showItems() {
    console.log("Meal includes:", this.items.join(", "));
  }
}

// Builder
class MealBuilder {
  constructor() {
    this.meal = new Meal();
  }
  addBurger() {
    this.meal.addItem("Burger");
    return this;
  }
  addDrink() {
    this.meal.addItem("Drink");
    return this;
  }
  addDessert() {
    this.meal.addItem("Dessert");
    return this;
  }
  build() {
    return this.meal;
  }
}

// Usage
const meal = new MealBuilder()
  .addBurger()
  .addDrink()
  .addDessert()
  .build();

meal.showItems(); // Output: Meal includes: Burger, Drink, Dessert
```

Separates the construction of complex objects from their representation, allowing step-by-step creation.

🔹 Use Cases:

1. Meal Ordering System (Burger, Drink, Dessert) – Customizes meal items using a builder.
2. Car Customization (Engine, Wheels, Interior) – Builds cars with varying configurations.
3. Document Generator (PDF, Word, HTML) – Creates documents with different formats but the same structure.
4. Query Builder (SQL Query Construction) – Helps in dynamically building complex database queries.

## 5. Prototype Pattern

The Prototype Pattern creates new objects by cloning an existing object (prototype) instead of creating instances from scratch. It is especially useful when object creation is costly or complex, and you want to avoid repeated instantiation overhead.

Key Features:
- Clones existing objects to create new ones.
- Reduces the cost of creating complex objects.
- Simplifies object creation when configuration is similar.

```js
// Prototype class
class Character {
  constructor(name, weapon) {
    this.name = name;
    this.weapon = weapon;
  }

  clone() {
    return new Character(this.name, this.weapon);
  }

  display() {
    console.log(`Character: ${this.name}, Weapon: ${this.weapon}`);
  }
}

// Usage
const original = new Character("Knight", "Sword");
original.display(); // Output: Character: Knight, Weapon: Sword

const clone1 = original.clone();
clone1.display(); // Output: Character: Knight, Weapon: Sword

// Customize clone
clone1.name = "Archer";
clone1.weapon = "Bow";
clone1.display(); // Output: Character: Archer, Weapon: Bow
```

Creates objects by cloning an existing object instead of instantiating new ones.

🔹 Use Cases:

1. Game Character Duplication – Copies characters with preset abilities and stats.
2. Document Templates – Creates new documents based on a predefined template.
3. Graphic Design (Shapes, Images, Icons) – Duplicates objects without reloading assets.
4. Workflow Automation (Cloning Predefined Tasks) – Automates task duplication.

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


## 1. Adapter Pattern
The Adapter Pattern acts as a bridge between incompatible interfaces, allowing them to work together. It translates one interface into another expected by the client.

Key Features:
- Enables compatibility between different interfaces.
- Acts as a wrapper to modify input/output formats.
- Useful for integrating legacy code with new systems.

```js
// Existing class (Old API)
class OldPaymentGateway {
  processPayment(amount) {
    console.log(`Processing payment of $${amount} through old gateway.`);
  }
}

// New interface expected by the client
class NewPaymentGateway {
  makePayment(amount) {
    console.log(`Processing payment of $${amount} through new gateway.`);
  }
}

// Adapter to make OldPaymentGateway compatible with NewPaymentGateway
class PaymentAdapter extends NewPaymentGateway {
  constructor(oldGateway) {
    super();
    this.oldGateway = oldGateway;
  }

  makePayment(amount) {
    this.oldGateway.processPayment(amount);
  }
}

// Usage
const oldGateway = new OldPaymentGateway();
const adapter = new PaymentAdapter(oldGateway);
adapter.makePayment(100); // Output: Processing payment of $100 through old gateway.
```

🔹 Use Cases:

1. Connecting a legacy system to a new API.
2. Converting XML-based APIs to JSON-based APIs.
3. Using third-party libraries with different interface requirements.
4. Adapting database drivers for different SQL engines.

## 2. Bridge Pattern
The Bridge Pattern decouples abstraction from implementation, allowing them to evolve independently. It is useful when a class has multiple dimensions of variations that need to be managed separately.

Key Features:
- Promotes loose coupling between abstraction and implementation.
- Makes code more scalable and flexible.
- Useful when dealing with different platforms or devices.

```js
// Implementor
class Renderer {
  renderShape() {}
}

// Concrete Implementations
class VectorRenderer extends Renderer {
  renderShape(shape) {
    console.log(`Rendering ${shape} as vector.`);
  }
}

class RasterRenderer extends Renderer {
  renderShape(shape) {
    console.log(`Rendering ${shape} as raster.`);
  }
}

// Abstraction
class Shape {
  constructor(renderer) {
    this.renderer = renderer;
  }
  draw() {}
}

// Refined Abstractions
class Circle extends Shape {
  constructor(renderer) {
    super(renderer);
  }
  draw() {
    this.renderer.renderShape("Circle");
  }
}

// Usage
const vectorCircle = new Circle(new VectorRenderer());
vectorCircle.draw(); // Output: Rendering Circle as vector.

const rasterCircle = new Circle(new RasterRenderer());
rasterCircle.draw(); // Output: Rendering Circle as raster.
```

🔹 Use Cases:

1. Supporting multiple rendering engines (Vector vs. Raster).
2. Separating UI elements from platform-specific rendering.
3. Decoupling business logic from different data sources.
4. Managing device-independent graphics frameworks.

## 3. Composite Pattern
The Composite Pattern is used to treat individual objects and groups of objects uniformly. It enables a tree-like structure where leaf and composite nodes are handled the same way.

Key Features:
- Treats individual objects and compositions uniformly.
- Useful for tree structures like file systems, UIs, or hierarchies.
- Simplifies client code by handling groups of objects in the same way.

```js
// Component Interface
class Graphic {
  draw() {}
}

// Leaf
class Circle extends Graphic {
  draw() {
    console.log("Drawing a Circle");
  }
}

// Composite
class Group extends Graphic {
  constructor() {
    super();
    this.children = [];
  }
  add(graphic) {
    this.children.push(graphic);
  }
  draw() {
    this.children.forEach((graphic) => graphic.draw());
  }
}

// Usage
const circle1 = new Circle();
const circle2 = new Circle();

const group = new Group();
group.add(circle1);
group.add(circle2);

group.draw();
// Output:
// Drawing a Circle
// Drawing a Circle
```

🔹 Use Cases:

1. File system representation (Folders & Files).
2. UI Component trees (Buttons, Panels, Windows).
3. Managing organizational hierarchies.
4. Building complex graphical objects in games.

## 4. Decorator Pattern
The Decorator Pattern dynamically adds behavior or responsibilities to objects without modifying their code. It follows the principle of open-closed design.

Key Features:
- Allows behavior modification at runtime.
- Enhances existing functionality without altering base class code.
- Supports multiple decorators stacked on an object.

```js
// Base Component
class Coffee {
  cost() {
    return 5;
  }
}

// Decorator
class Milk extends Coffee {
  constructor(baseCoffee) {
    super();
    this.baseCoffee = baseCoffee;
  }

  cost() {
    return this.baseCoffee.cost() + 2;
  }
}

// Usage
const simpleCoffee = new Coffee();
console.log(simpleCoffee.cost()); // Output: 5

const milkCoffee = new Milk(simpleCoffee);
console.log(milkCoffee.cost());
```

🔹 Use Cases:
1. Adding features to UI components dynamically (e.g., tooltips, borders).
2. Implementing logging, caching, or authentication without modifying existing classes.
3. Extending functionality of graphical editors (e.g., adding filters, effects).
4. Enhancing game characters with power-ups.

## 5. Facade Pattern
The Facade Pattern provides a simplified interface to a larger, more complex system.

Key Features:
- Hides the complexity of subsystems.
- Provides a unified, high-level interface.
- Improves code readability and maintainability.

```js
// Complex Subsystem
class CPU {
  start() {
    console.log("CPU starting...");
  }
}

class Memory {
  load() {
    console.log("Loading memory...");
  }
}

class HardDrive {
  read() {
    console.log("Reading data from Hard Drive...");
  }
}

// Facade
class Computer {
  constructor() {
    this.cpu = new CPU();
    this.memory = new Memory();
    this.hardDrive = new HardDrive();
  }

  start() {
    console.log("Starting computer...");
    this.cpu.start();
    this.memory.load();
    this.hardDrive.read();
  }
}

// Usage
const myComputer = new Computer();
myComputer.start();
// Output:
// Starting computer...
// CPU starting...
// Loading memory...
// Reading data from Hard Drive...

```
🔹 Use Cases:
1. Simplifying database or API interactions.
2. Providing a unified interface for complex subsystems.
3. Managing third-party library integrations with a clean API.
4. Creating simplified service interfaces in web applications.

## 6. Proxy Pattern
The Proxy Pattern acts as a surrogate or placeholder for another object, controlling access to it.

Key Features:
- Controls access to an object.
- Can add security, caching, or logging functionalities.
- Helps in implementing lazy loading and remote proxies.

```js
// Real Subject
class RealImage {
  constructor(filename) {
    this.filename = filename;
    this.loadFromDisk();
  }

  loadFromDisk() {
    console.log(`Loading ${this.filename}`);
  }

  display() {
    console.log(`Displaying ${this.filename}`);
  }
}

// Proxy
class ProxyImage {
  constructor(filename) {
    this.filename = filename;
    this.realImage = null;
  }

  display() {
    if (!this.realImage) {
      this.realImage = new RealImage(this.filename);
    }
    this.realImage.display();
  }
}

// Usage
const image = new ProxyImage("photo.jpg");
image.display(); // Output: Loading photo.jpg, Displaying photo.jpg
image.display(); // Output: Displaying photo.jpg
```
🔹 Use Cases:
1. Implementing virtual proxies for lazy loading.
2. Adding security layers (e.g., authentication).
3. Managing expensive object creation.
4. Controlling access to remote objects.

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