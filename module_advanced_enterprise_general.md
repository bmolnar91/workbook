# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

WIP

In software engineering, **multi-tier architecture** (often referred to as **n-tier architecture**) is a client-server architecture in which, the presentation, the application processing and the data management are logically separate processes. For example, an application that uses middleware to service data requests between a user and a database employs multi-tier architecture. The most widespread use of "multi-tier architecture" refers to three-tier architecture.

N-tier architecture is also called multi-tier architecture because the software is engineered to have the processing, data management, and presentation functions **physically and logically separated**. That means that these different functions are **hosted on several machines or clusters**, ensuring that services are provided without resources being shared and, as such, these services are delivered at top capacity.

Not only does your software gain from being able to get services at the best possible rate, but it’s also easier to manage. This is because when you work on one section, the changes you make will not affect the other functions. And if there is a problem, you can easily pinpoint where it originates.

Three tiers:

1. **Presentation tier**:
   The top-most level of the application is the **User Interface**. The main function of the interface is to translate tasks and result to something the user can understand.
2. **Logic tier**:
   This layer coordinates the application, processes commands, makes logical decisions and evaluations, and performs calculations. It also moves and processes data between two surrounding layers.
3. **Data tier**:
   Here information is stored and retrieved from a database or file system. The information is then passed back to the logic tier for processing, and then eventually back to the user.

**The separate physical location of these tiers is what differentiates n-tier architecture from the _model-view-controller_ framework that only separates presentation, logic, and data tiers _in concept_.** N-tier architecture also differs from MVC framework in that the former has a middle layer or a logic tier, which facilitates all communications between the different tiers. When you use the MVC framework, the interaction that happens is triangular; instead of going through the logic tier, it is the control layer that accesses the model and view layers, while the model layer accesses the view layer.

This is not to say that you can only use either the MVC framework or the n-tier architecture. There are a lot of software that brings together these two frameworks. For instance, you can use the n-tier architecture as the overall architecture, or use the MVC framework in the presentation tier.

Benefits: secure, easy to manage, scalable (between tiers), flexible (inside tiers), reusable code.

> There are n-tier architecture models that have more than three tiers. E.g.: Services + Business domain + Presentation tier + Client tier.

#### What are microservices? Advantages and disadvantages?

#### What is Separation of Concerns?

WIP

The **separation of concerns (SoC)** is one of the most fundamental principles in software development.

It is so crucial that 2 out of 5 SOLID principles (**Single Responsibility** and **Interface Segregation**) are direct derivations from this concept.

The principle is simple: don't write your program as one solid block, instead, **break up the code into chunks** that are finalized tiny pieces of the system each able to complete a simple distinct job.

#### What is a layered design and why is it important in enterprise applications?

Modern enterprise applications can be large and daunting. The sheer amount of users, data, transactions, options, business cases, components, interacting systems, and a host of other factors, make designing business applications require a great deal of expertise. There are many examples of enterprise software that grew too complex, unmanageable, and fragile due to implementation, that did not account for change. It is for this reason that an effective enterprise application should be divided into layers.

The layered architecture is the simplest form of software architectural pattern. If you are going to design a rudimentary application where the user count is very low ( < 100–200 ) and you are sure that there won't be too much requirement changes after you go live, this is the best software architecture pattern to use.

Layered architecture patterns are **n-tiered patterns** where the components are organized in horizontal layers. All the components are interconnected but do not depend on each other.

There are 4 layers in this architecture. From top to bottom:

1. **Presentation layer**: It contains all categories related to the presentation layer.
2. **Business layer**: It contains business logic.
3. **Persistence layer**: Used for handling functions like object-relational mapping.
4. **Database layer**: This is where all the data is stored.

Pros:

- It is easy to test as components belong to specific layers. As such, they can be tested separately.
- It is simple and easy to implement because naturally, most applications work in layers.

Cons:

- Although changes can be done to a particular layer, it is not easy because the application is a singular unit. Also, the coupling between layers tends to make it harder. This also makes it difficult to scale.
- It must be deployed as a singular unit thus a change to a particular layer means the whole system must be redeployed.
- The larger is it, the more resources it requires for requests to go through multiple layers and thus will cause performance issues.

#### What is Dependency Injection?

Classes have "dependencies" they call methods on. Most people call them "variables" or more precisely "instance variables".

You could set the dependency (variable) via a setter method or even via reflection, you should choose your way. But using constructors is the most popular one.

You can have the dependency be an interface or an abstract class and then polymorphically pass in some implementation.

Also DI facilitates a very important principle, **Separation of Concerns**, because:

- Many times is not a given class' responsibility to instantiate the things inside it.
- Your code will be more modular, as the outside world can decide what exactly it should be (to make it super modular you could make it an interface).

Dependency Injection can also refer to a **software library** that provides DI functionality and allows automating many of the tasks involved in Object Composition, Interception, and Lifetime Management. DI Containers are also known as Inversion of Control (IoC) Containers. (E.g. Spring Boot, ASP.NET Core).

At the very least, a DI Container allows Auto-Wiring, which is the ability to automatically compose an object graph from maps between **Abstractions** and concrete types by making use of the types' **metadata** (reflection?) supplied by the compiler and its runtime environment.

**This typically means that a DI Container will analyze a type's constructor and will inject dependencies into it, without the need of having to specify each constructor argument manually.**

#### What is the DAO pattern? When and how to implement?

WIP

**Data access object (DAO)** is a pattern that provides an abstract interface to some type of database or other persistence mechanism.

By mapping application calls to the persistence layer, the DAO provides some specific data operations without exposing details of the database. This isolation supports the single responsibility principle.

It separates what data access the application needs from how these needs can be satisfied with a specific DBMS, database schema, etc.

#### What is SOA? When to use?

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

WIP

**Testing methods**:

- **Black-box testing**: Testing the functionality of the software without knowing its internal code structure. No programming knowledge is required.
- **White-box testing**: Testing the software itself with the knowledge of its internal structure. Basically you know the code and write the tests to test the code.

**Levels of testing**:

- **Unit test** -- Test individual component: Specify and test one point of the contract of **a single method** of a class. This should have a very narrow and well defined scope. Complex dependencies and interactions to the outside world are **stubbed** or **mocked**.
- **Integration test** -- Test component groups: Test the correct inter-operation of multiple subsystems. There is whole spectrum there, from testing integration between two classes, to testing integration with the production environment.
- **System test** -- Test the integrated System: Tests a system as a **black box**. Dependencies on other systems are often **mocked** or **stubbed** during the test (otherwise it would be more of an integration test).
- **Acceptance test** -- Test the final System: Test that a feature or use case is correctly implemented. It is similar to an integration test, but with a **focus on the use case** to provide rather than on the components involved.

**Types of testing**:

- **Functional testing**:
  - Functional Testing is the type of testing done against the **business requirements** of application. It is a **black box type** of testing (mostly).
  - **Smoke test** (aka **sanity check**): A simple integration test where we just check that when the _system under test (SUT)_ is invoked it returns normally and does not blow up. Smoke testing is **an analogy with plumbing**, where a system of pipes is literally filled by smoke and then checked visually. If anything smokes, the system is leaky.
  - **Regression test**: A test that was written **when a bug was fixed**. It ensures that this specific bug will not occur again. The full name is "non-regression test". It can also be a test made **prior to changing an application** to make sure the application provides the same outcome.
- **Non-functional testing**:
  - Done against the **non functional requirements**. Most of the criteria are not consider in functional testing so it is used to check the readiness of a system.
  - Performance testing
  - Security testing
  - Stress testing

#### What is code coverage? Why is it used? How you can measure?

WIP

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

WIP

#### What is a test case? What is an assertion? Give examples!

WIP

#### What is TDD? What are the benefits?

WIP

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

WIP

#### What is arrange/act/assert pattern?

WIP

### DevOps

#### What is continuous integration? Why is CI important?

#### Why are tests important in the CI workflow?

#### Name some software that help the CI workflow!

#### What is Continuous Delivery?

#### What is Continuous Deployment?

#### What is DevOps?

### Software Methodologies

#### What kind of software-lifecycle models do you know?

WIP

- Agile development
- Waterfall model

#### What is a UML diagram? What kind of diagram types do you know?

WIP

The **Unified Modeling Language** is a standard visual modeling language intended to be used for:

- Modeling business and similar processes,
- Analysis, design, and implementation of software-based systems

There are two major kinds of UML diagram, structure diagrams and behavior diagrams:

- **Structure diagrams**: show the static structure of the system and its parts on different abstraction and implementation levels and how they are related to each other. The elements in a structure diagram represent the meaningful concepts of a system, and may include abstract, real world and implementation concepts.
- **Behavior diagrams**: show the dynamic behavior of the objects in a system, which can be described as a series of changes to the system over time.

I've used **Class Diagrams** (structure) extensively, and **Event Diagrams** (behavior) occasionally.

> Draw.io > PlantUML

#### What is a UML class diagram? What are the typical elements?

WIP

Before implementating a bunch of classes, you'll want to have **a conceptual understanding of the system** — that is, what classes do I need? What functionality and information will these classes have? How do they interact with one another? Who can see these classes? And so on.

That's where class diagrams come in. Class diagrams are a neat way of visualizing the classes in your system before you actually start coding them up. They're **a static representation of your system structure**.

Why do we need class diagrams:

1. Planning and modeling ahead of time make programming much easier.
2. Besides that, making changes to class diagrams is easy, whereas coding differnent functionality after the fact is kind of annoying.
3. When someone wants to build a house, they don't just grab a hammer and get to work. They need to have a **blueprint** — a design plan — so they can ANALYZE & modify their system.
4. You don't need much technical/language-specific knowledge to understand it.

**UML Class Notation**:

A class is represented as a box with 3 compartments. The uppermost one contains the **class name**. The middle one contains the **STATE = class attributes** and the last one contains the **BEHAVIOR = class operations** (methods).
Each attribute has a _type_. Each operation has a _signature_.

**Class visibility**:

- \- private
- ~ package
- \# protected
- \+ public

**Relationships**:

- **Association**:
  - Associations are relationships between classes in a UML Class Diagram. They are represented by **a solid line between classes**. Associations are typically named using a verb or verb phrase which reflects the real world problem domain.
  - General association is simply a solid line.
  - E.g. `Airplane -- Ticket`
- **Inheritence**:
  - Represents an **"is-a" relationship**.
  - An abstract class name is shown in italics.
  - Represented by **a solid line + an empty arrow** pointing to the extended class.
  - E.g. `Square --|> Rectangle`
- **Realization**:
  - Same as Inheritence but with interfaces.
  - Interface is shown between two diamond operators + name in italics: `<<interface>> _IMyInterface_`
  - Represented by **a dashed line + an empty arrow** pointing to the implemented interface.
  - E.g. `MotorCar ..|> Car`
- **Aggregation**:
  - A special type of association.
  - It represents a **"has-a" relationship**.
  - Objects of Class1 and Class2 have **separate lifetimes**.
  - Represented by **a solid line + an empty diamond** pointing to the aggregator class.
  - E.g. `Tortoise --o Creep`
- **Composition**
  - A special type of aggregation where parts are destroyed when the whole is destroyed.
  - It represents a **"has-a" relationship**.
  - Objects of Class1 and Class2 have the **same lifetimes**.
  - Represented by **a solid line + a filled diamond** pointing to the composite class.
  - E.g. `Heart --* Human`
- Dependency:
  - An object of one class might use an object of another class in the code of a method. If the object is **not stored in any field**, then this is modeled as a dependency relationship.
  - A special type of association.
  - Exists between two classes if **changes to the definition of one may cause changes to the other** (but not the other way around).
- Cardinality:
  - Cardinality is expressed in terms of:
    - one to one
    - one to many
    - many to many
  - E.g.:
    - `1`: ecactly one
    - `0..1`: zero to one
    - `*`: zero or more
    - `1..*`: at least one
    - `{ordered}`: ordered

#### What kind of design patterns do you know? Bring at least 3 examples.

WIP

In software engineering, a design pattern is **a general reusable solution** to a commonly occurring problem in software design. It is not a finished design that can be transformed directly into code. It is **a description or template** for how to solve a problem that can be used in many different situations. Design patterns are **formalized best practices** that the programmer can use to solve common problems when designing an application or system.

Object-oriented design patterns are traditionally classified under three categories:

- **Creational**: designing how objects can be created. This often involves isolating the details of object creation so your code isn't dependent on what types of objects there are, and thus doesn't have to be changed when you add a new type of object. E.g. Factory pattern.
- **Structural**: designing objects to satisfy particular project constraints. These work with the way objects are connected with other objects to ensure that changes in the system don't require changes to those connections. E.g. Decorator patter.
- **Behavioral**: designing objects that handle particular types of actions within a program. These encapsulate processes that you want to perform, such as interpreting a language, fulfilling a request, moving through a sequence (as in an iterator), or implementing an algorithm. E.g. Iterator pattern.

1. **Factory Method pattern** (creational):
   - A normal factory produces goods; a software factory produces objects. And not just that — it does so without specifying the exact class of the object to be created. To accomplish this, objects are created by calling a factory method instead of calling a constructor.
   - There's nothing wrong with using `new` to create objects but it comes with the baggage of **tightly coupling** our code to the concrete implementation class, which can occasionally be problematic.
   - Static factory methods returning the same type as the containing class are substitutes for constructors, with several advantages:
     - Unlike constructors, they have **names**. In some cases this makes our code **more readable**. More importantly, it is possible to have **two different factory methods with the same signature**.
     - Unlike constructors, they are **not required to create a new object** each time they're invoked. We can add features like pooling, caching, lazy loading, or other extras and limitations. Singleton's `getInstance()` is a good example for this.
     - Unlike constructors, they can **return an object of any subtype** of their return type.
2. **Singleton pattern** (creational):
   - The singleton pattern is used to limit creation of a class to only one object. This is beneficial when one (and only one) object is needed to coordinate actions across the system.
   - There are several examples of where only a single instance of a class should exist, including caches, loggers, etc.
3. **Iterator pattern** (behavioral):
   - The iterator pattern is a design pattern in which an iterator is used to traverse a container and access the container's elements. The iterator pattern decouples algorithms from containers in most cases.
   - For example, the hypothetical algorithm _SearchForElement_ can be implemented generally using a specified type of iterator rather than implementing it as a container-specific algorithm. This allows _SearchForElement_ to be used on any container that supports the required type of iterator.

#### What is the purpose of the Iterator Pattern?

WIP

The purpose of the iterator pattern is to abstract away the underlying structure in which the data are kept. Data-structure can be an array, a tree, a list, etc.

Its important methods in C#:

- `Current` (property)
- `MoveNext()`
- `Reset()`
- (`Dispose()`)

Uses the `yield return` keyword.

You can enumerate objects that import the `IEnumerable` interface with the `foreach` statement. It calls the `GetEnumerator()` method of the class. This `IEnumerator` then iterates through the data structure, yielding items one by one until there's no Next.

Where To Apply Iterator Pattern:

- When you want to access a collection of objects without exposing its internal representation.
- When there are multiple traversals of objects need to be supported in the collection.

#### What do you know about the SOLID principles?

The SOLID principles were first conceptualized by Robert C. Martin. These design principles encourage us to create more **maintainable**, **understandable**, and **flexible** software. Consequently, as our applications **grow in size**, we can **reduce their complexity** and save ourselves a lot of headaches further down the road.

The following 5 concepts make up our SOLID principles:

1. **Single Responsibility** principle:
   - A class should only have **one responsibility**. Furthermore, it should only have **one reason to change**.
   - Benefits:
     - Testing: A class with one responsibility will have far fewer test cases
     - Lower coupling: Less functionality in a single class will have fewer dependencies
     - Organization: Smaller, well-organized classes are easier to search than monolithic ones
   - Book / BookPrinter example
2. **Open/Closed** principle:
   - Open for _extension_, Closed for _modification_
   - In doing so, we stop ourselves from modifying existing code and causing potential new bugs
   - Guitar example
3. **Liskov Substitution** principle:
   - If class _A_ is a subtype of class _B_, then we should be able to replace _B_ with A without disrupting the behavior of our program
   - Electric car / Motorcar example
4. **Interface Segregation** principle:
   - Larger interfaces should be split into smaller ones.
   - By doing so, we can ensure that implementing classes only need to be concerned about the methods that are of interest to them.
   - Zookeeper / BearPetter example
5. **Dependency Inversion** principle:
   - The DIP is neither dependency injection (DI) nor inversion of control (IoC). Even so, they all work great together.
   - Simply put, DI is about making software components to explicitly declare their dependencies (or collaborators) through their APIs, instead of acquiring them by themselves.
   - The principle of Dependency Inversion refers to the **decoupling** of software modules.
   - This way, instead of high-level modules depending on low-level modules, both will depend on **abstractions**.
   - With DI, the responsibility of providing the component dependencies and wiring object graphs is transferred from the components to the underlying _injection framework_.

> In traditional software development, high-level components depend on low-level ones. Thus, it's hard to reuse the high-level components. The DIP is about inverting the classic dependency between high-level and low-level components by abstracting away the interaction between them.

#### How would you separate data storage code and business logic code (which uses stored data) in an application?

## Computer science

### Data Structures

#### What is the difference between Stack and Queue data structure?

#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?

#### What are trees? What are binary trees? What are binary search trees?

#### How can you store graphs in programs? What are the advantages/disadvantages per each?

#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?

#### How does dictionary work?

#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

### Algorithms

#### What is QuickSort? Describe the main logic of this sorting algorithm.

WIP

## Software design

### Security

#### What is OAuth2?

#### What is Basic Authentication?

#### What is CORS, why it’s needed in browsers?

#### How can you initialize a CSRF attack?

#### What is JWT used for? Where to store it on client side?

### Threaded programming

#### When do you need to use threads in an application?

#### What is a daemon thread?

#### What is the difference between concurrent and parallel execution of code?

#### What is the most important problem developers are faced when using threads?

#### In what kind of situations can deadlocks occur?

#### What are possible ways to prevent deadlocks from occurring?

#### What does critical section or critical region mean in the context of concurrent programming?
