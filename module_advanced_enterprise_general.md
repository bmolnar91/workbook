# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

WIP

In software engineering, multi-tier architecture (often referred to as n-tier architecture) is a client-server architecture in which, the presentation, the application processing and the data management are logically separate processes. For example, an application that uses middleware to service data requests between a user and a database employs multi-tier architecture. The most widespread use of "multi-tier architecture" refers to three-tier architecture.

N-tier architecture is also called multi-tier architecture because the software is engineered to have the processing, data management, and presentation functions **physically and logically separated**. That means that these different functions are **hosted on several machines or clusters**, ensuring that services are provided without resources being shared and, as such, these services are delivered at top capacity.

Not only does your software gain from being able to get services at the best possible rate, but it’s also easier to manage. This is because when you work on one section, the changes you make will not affect the other functions. And if there is a problem, you can easily pinpoint where it originates.

Three tiers:

1. Presentation tier:
   The top-most level of the application is the **User Interface**. The main function of the interface is to translate tasks and result to something the user can understand.
2. Logic tier:
   This layer coordinates the application, processes commands, makes logical decisions and evaluations, and performs calculations. It also moves and processes data between two surrounding layers.
3. Data tier:
   Here information is stored and retrieved from a database or file system. The information is then passed back to the logic tier for processing, and then eventually back to the user.

**The separate physical location of these tiers is what differentiates n-tier architecture from the _model-view-controller_ framework that only separates presentation, logic, and data tiers _in concept_.** N-tier architecture also differs from MVC framework in that the former has a middle layer or a logic tier, which facilitates all communications between the different tiers. When you use the MVC framework, the interaction that happens is triangular; instead of going through the logic tier, it is the control layer that accesses the model and view layers, while the model layer accesses the view layer.

This is not to say that you can only use either the MVC framework or the n-tier architecture. There are a lot of software that brings together these two frameworks. For instance, you can use the n-tier architecture as the overall architecture, or use the MVC framework in the presentation tier.

Benefits: secure, easy to manage, scalable (between tiers), flexible (inside tiers), reusable code.

//And there are n-tier architecture models that have more than three tiers. E.g.: Services + Business domain + Presentation tier + Client tier//

#### What are microservices? Advantages and disadvantages?

#### What is Separation of Concerns?

WIP

The separation of concerns (SoC) is one of the most fundamental principles in software development.

It is so crucial that 2 out of 5 SOLID principles (Single Responsibility and Interface Segregation) are direct derivations from this concept.

The principle is simple: don't write your program as one solid block, instead, break up the code into chunks that are finalized tiny pieces of the system each able to complete a simple distinct job.

#### What is a layered design and why is it important in enterprise applications?

Modern enterprise applications can be large and daunting. The sheer amount of users, data, transactions, options, business cases, components, interacting systems, and a host of other factors, make designing business applications require a great deal of expertise. There are many examples of enterprise software that grew too complex, unmanageable, and fragile due to implementation, that did not account for change. It is for this reason that an effective enterprise application should be divided into layers.

The layered architecture is the simplest form of software architectural pattern. If you are going to design a rudimentary application where the user count is very low ( < 100–200 ) and you are sure that there won't be too much requirement changes after you go live, this is the best software architecture pattern to use.

Layered architecture patterns are **n-tiered patterns** where the components are organized in horizontal layers. All the components are interconnected but do not depend on each other.

There are 4 layers in this architecture. From top to bottom:

1. Presentation layer: It contains all categories related to the presentation layer.
2. Business layer: It contains business logic.
3. Persistence layer: Used for handling functions like object-relational mapping.
4. Database layer: This is where all the data is stored.

Pros:

- It is easy to test as components belong to specific layers. As such, they can be tested separately.
- It is simple and easy to implement because naturally, most applications work in layers.

Cons:

- Although changes can be done to a particular layer, it is not easy because the application is a singular unit. Also, the coupling between layers tends to make it harder. This also makes it difficult to scale.
- It must be deployed as a singular unit thus a change to a particular layer means the whole system must be redeployed.
- The larger is it, the more resources it requires for requests to go through multiple layers and thus will cause performance issues.

#### What is Dependency Injection?

#### What is the DAO pattern? When and how to implement?

#### What is SOA? When to use?

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

#### What is code coverage? Why is it used? How you can measure?

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

#### What is a test case? What is an assertion? Give examples!

#### What is TDD? What are the benefits?

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

#### What is arrange/act/assert pattern?

### DevOps

#### What is continuous integration? Why is CI important?

#### Why are tests important in the CI workflow?

#### Name some software that help the CI workflow!

#### What is Continuous Delivery?

#### What is Continuous Deployment?

#### What is DevOps?

### Software Methodologies

#### What kind of software-lifecycle models do you know?

#### What is a UML diagram? What kind of diagram types do you know?

#### What is a UML class diagram? What are the typical elements?

#### What kind of design patterns do you know? Bring at least 3 examples.

#### What is the purpose of the Iterator Pattern?

#### What do you know about the SOLID principles?

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
