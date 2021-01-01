# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

WIP

In software engineering, **multi-tier architecture** (often referred to as **n-tier architecture**) is a **client-server architecture** in which, the presentation, the application processing and the data management are logically separate processes. For example, an application that uses middleware to service data requests between a user and a database employs multi-tier architecture. The most widespread use of "multi-tier architecture" refers to three-tier architecture.

N-tier architecture is also called multi-tier architecture because the software is engineered to have the processing, data management, and presentation functions **_physically_ and logically separated**. That means that these different functions are **hosted on several machines** or clusters, ensuring that services are provided without resources being shared and, as such, these services are delivered at top capacity.

Not only does your software gain from being able to get services at the best possible rate, but it's also easier to manage. This is because when you work on one section, the changes you make will not affect the other functions. And if there is a problem, you can easily pinpoint where it originates.

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

WIP

**Microservices** got into fashion very lately, only in the 2010s. There are two important factors in its success:

- The birth of the **cloud**. Cloud services (like Amazon Web Services, Microsoft Azure, etc.) enable to create/destroy virtual servers with a click. This enabled easily creating distributed systems instead of the dominant _monolith architecture_ (a single big codebase), and promoted virtualization and new integration and deployment techniques.
- The spread of **agile** methodologies. Agile introduced smaller, more autonomous and heterogeneous teams. These teams can develop new features faster if they have less and more clear dependencies with their environment. Such an organizational structure has its impact on software architecture as well (see Conway's law).

**What are Microservices?**

There is a widely-cited definition by Adrian Cockcroft, former chief cloud architect at Netflix, that **microservices architecture (MSA)** is a service oriented architecture composed of loosely coupled elements that have _bounded contexts_. This is not much of help without lengthy essays on each concepts involved, so let's put definitions away and collect some aspects of microservices:

- They are **separate programs** communicating over a network (usually using basic HTTP protocol)
- Each service has a **small and explicit problem domain** and responsibility
- Each service has their **separate data store** (when needed)
- Services are **independently deployable** and easily **replaceable**

**What are the strenghts?**

- Faster feature development: decisions are made by smaller, more autonomous teams
- Better scalability: deployment and load balancing is based on small components
- More robustness: services are designed with inevitable failures in mind
- More flexibility: it is possible to use different (newer or more adequate) technologies or even languages at any point

**What are the drawbacks?**

- Instead of referencing other components directly, you have to deal a lot with the communication between services.
- In a distributed system you have to deal with a lot of problems that do not occur inside a single application, e.g. network latency and failures, asynchronous communication, state inconsistencies. In addition, there are exotic types of errors coming from the distributed character of such systems (like the so-called _cascading failure_) which are very hard to predict and prevent.
- Extra services and tools that are optional for ordinary projects (like the need for continuous delivery and deployment monitoring tools) become a must.
- A flawed or changing service structure can be harder to redesign when teams, APIs, and codebases are already in place.

#### What is Separation of Concerns?

WIP

The **separation of concerns (SoC)** is one of the most fundamental principles in software development.

It is so crucial that 2 out of 5 SOLID principles (**Single Responsibility** and **Interface Segregation**) are direct derivations from this concept.

The principle is simple: don't write your program as one solid block, instead, **break up the code into chunks** that are finalized tiny pieces of the system each able to complete a simple distinct job.

#### What is a layered design and why is it important in enterprise applications?

Modern enterprise applications can be large and daunting. The sheer amount of users, data, transactions, options, business cases, components, interacting systems, and a host of other factors, make designing business applications require a great deal of expertise. There are many examples of enterprise software that grew too complex, unmanageable, and fragile due to implementation, that did not account for change. It is for this reason that an effective enterprise application should be divided into layers.

The layered architecture is the simplest form of **software architectural pattern**. If you are going to design a rudimentary application where the user count is very low ( < 100–200 ) and you are sure that there won't be too much requirement changes after you go live, this is the best software architecture pattern to use.

Layered architecture patterns are **n-tiered patterns** where the components are organized in horizontal layers. All the **components are interconnected but do not depend on each other**.

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
- It must be deployed as a singular unit thus a **change to a particular layer means the whole system must be redeployed**.
- The larger is it, the more resources it requires for requests to go through multiple layers and thus will cause performance issues.

#### What is Dependency Injection?

Classes have "dependencies" they call methods on. Most people call them "variables" or more precisely "instance variables".

You could set the dependency (variable) via a setter method or even via reflection, you should choose your way. But using constructors is the most popular one.

You can have the dependency be an interface or an abstract class and then polymorphically pass in some implementation.

Also DI facilitates a very important principle, **Separation of Concerns**, because:

- Many times is not a given class' responsibility to instantiate the things inside it.
- Your code will be more **modular**, as the outside world can decide what exactly it should be (to make it super modular you could make it an interface).

Dependency Injection can also refer to a **software library** that provides DI functionality and allows automating many of the tasks involved in Object Composition, Interception, and Lifetime Management. DI Containers are also known as Inversion of Control (IoC) Containers. (E.g. Spring Boot, ASP.NET Core).

At the very least, a DI Container allows **Auto-Wiring**, which is the ability to automatically compose an object graph from maps between **Abstractions** and concrete types by making use of the types' **metadata** (reflection?) supplied by the compiler and its runtime environment.

**This typically means that a DI Container will analyze a type's constructor and will inject dependencies into it, without the need of having to specify each constructor argument manually.**

#### What is the DAO pattern? When and how to implement?

WIP

**Data access object (DAO)** is a pattern that provides an abstract interface to some type of database or other persistence mechanism.

By mapping application calls to the persistence layer, the DAO provides some specific data operations without exposing details of the database. This isolation supports the single responsibility principle.

It separates what data access the application needs from how these needs can be satisfied with a specific DBMS, database schema, etc.

#### What is SOA? When to use?

WIP

**Service-oriented architecture (SOA)** is a type of software design that makes software components reusable using service interfaces that use a common communication language over a network.

A **service** is a self-contained unit of software functionality, or set of functionalities, designed to complete a specific task such as retrieving specified information or executing an operation. It contains the code and data integrations necessary to carry out a complete, discrete business function and can be accessed remotely and interacted with or updated _independently_.

> In other words, SOA integrates software components that have been separately deployed and maintained and allows them to communicate and work together to form an application across different systems.

In service-oriented architecture, services communicate using a system of **loose coupling**. This is a way of interconnecting _components_ (also called _elements_) in a system or network so that they can pass information or coordinate a process while relying on each other as little as possible. This, in effect, creates a new app.

Benefits over monolithic approach:

- **Faster time to market and greater flexibility**: The reusable-services aspect of SOA makes it much easier and faster to assemble applications, instead of developers starting from scratch each time as would be the case with monolithic applications.
- **Use legacy infrastructure in new markets**: SOA makes it easier for developers to take the functionality of one platform or environment and scale and extend it to new ones.
- **Reduced costs from greater agility and more efficient development**
- **Easy maintenance**: Because all services are self-contained and independent, they can be modified and updated as needed without affecting other services.
- **Scalability**: Since SOA permits services to run across multiple services, platforms, and programming languages, scalability is greatly increased. And SOA uses a standardized communication protocol, allowing enterprises to decrease interaction between clients and services. Lowering this level of interaction allows apps to be scaled with less pressure and inconvenience.
- **Greater reliability**: Since it's easier to debug smaller services than large code, SOA generates apps that are more reliable.
- **Convenience of availability**: SOA facilities are available to anyone.

**SOA vs. microservices**:

The concept of services introduced by service-oriented architecture has become what is now a central component of modern cloud computing and virtualization in things like **middleware** and **microservices**.

Because of their similarities, SOA and microservices are often confused. The main characteristic that can help differentiate between them is their **scope**: SOA is an enterprise-wide approach to _architecture_, while microservices is an _implementation strategy_ within application development teams.

They also communicate to their respective components differently, with SOA using an **ESB** (enterprise service bus: performs the integration between a centralized component and backend systems and then make them available as service interfaces) while microservices can communicate with each other **statelessly, through language-agnostic APIs**. The language-agnostic aspect of APIs in microservices also allows dev teams to choose what tools they want to work with. In these ways, microservices can be more tolerant and flexible.

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

WIP

**Testing methods**:

- **Black-box testing**: Testing the functionality of the software without knowing its internal code structure.
- **White-box testing**: Testing the software itself with the knowledge of its internal structure. Basically you know the code and write the tests to test the code.

**Levels of testing**:

1. **Unit test** -- Test individual component (**low-level**): Specify and test one point of the contract of **a single method** of a class. This should have a very narrow and well defined scope. Complex dependencies and interactions to the outside world are **stubbed** or **mocked**. Some characteristics:
   - examine a single class,
   - require **just the source code** of the application, instead of a running instance,
   - are **fast**,
   - are not affected by external systems, e.g. web services or databases, and
   - perform little or no I/O, e.g. no real database connections -- **no side-effects**.
   - **Positive Testing**: testing the system by giving the **valid data**.
   - **Negative Testing**: testing the system by giving the **invalid data**.
2. **Integration test** -- Test component groups: Test the correct inter-operation of multiple subsystems. There is whole spectrum there, from testing integration between two classes, to testing integration with the production environment.
3. **System test** -- Test the integrated System: Tests a system as a **black box**. Dependencies on other systems are often **mocked** or **stubbed** during the test (otherwise it would be more of an integration test).
4. **Acceptance test** -- Test the final System: Test that a feature or use case is correctly implemented. It is similar to an integration test, but with a **focus on the use case** to provide rather than on the components involved.

**Types of testing**:

- **Functional testing**:
  - Functional Testing is the type of testing done against the **business requirements** of application. It is a **black box type** of testing (mostly).
  - **Smoke test** (aka **sanity check**): A simple integration test where we just check that when the _system under test (SUT)_ is invoked it returns normally and does not blow up. Smoke testing is **an analogy with plumbing**, where a system of pipes is literally filled by smoke and then checked visually. If anything smokes, the system is leaky.
  - **Regression test**: A test that was written **when a bug was fixed**. It ensures that this specific bug will not occur again. The full name is "non-regression test". It can also be a test made **prior to changing an application** to make sure the application provides the same outcome.
- **Non-functional testing**:
  - Done against the **non functional requirements**. Most of the criteria are not consider in functional testing so it is used to check the readiness of a system.
  - Performance testing
  - Stress testing
  - Security testing
  - etc.

#### What is code coverage? Why is it used? How you can measure?

WIP

Code Coverage is a measurement of how many lines/blocks/arcs of your code are executed while the automated tests are running.

While code coverage is a good metric of how much testing you are doing, it is not necessarily a good metric of how well you are testing your product. There are other metrics you should use along with code coverage to ensure the quality.

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

WIP

Unit testing means testing units _independently_, so in some cases we need to isolate the component under test using what Martin Fowler calls **test doubles** (dummies, stubs, fakes, mocks).

In short, mocking is creating units (class instances) that **simulate the behaviour** of real units.

Mocking is the act of **removing external dependencies** from a unit test in order to **create a controlled environment** around it. Typically, we mock all other classes that interact with the class that we want to test. Common targets for mocking are:

- Database connections,
- Web services,
- Classes that are slow,
- Classes with side effects, and
- Classes with non-deterministic behavior.

Mocks and stubs are fake classes that replace these external dependencies. Most of the time, we're fine using only stubs.

**Stub**: A stub is a fake class that comes with **preprogrammed return values**. It's injected into the class (component) under test to give you absolute control over what's being tested as input. A typical stub is a **database connection** that allows you to mimic any scenario without having a real database.

**Mock**: A mock can be examined after the test is finished for its interactions with the class (component) under test. For example, you can ask it whether a method was called or how many times it was called. Typical mocks are **classes with side effects** that need to be examined, e.g. a class that sends emails or sends data to another external service.

We usually use libraries (Mockito, _NSubstitute_, Moq) that make mocking of objects easy. To make mocking possible you should use the **Dependency Injection** design pattern in your code!

Without a library, the easiest way would be to create an **inner class** that implements the interface, implement the methods to return the data that you want, then **use it in the test case**.

#### What is a test case? What is an assertion? Give examples!

WIP

A test case is represented by a single test method. An assertion asserts that the _expected_ outcome is the same as the _actual_ outcome.

Example:

```csharp
[Test]
public void ReadLines_Given1And1_ShouldReturnFirstLine()
{
    // Arrange
    int fromLine = 1;
    int toLine = 1;
    _filePartReader.Setup(SHORT_FILE_PATH, fromLine, toLine);
    // Act
    string expected = TestUtils.NormalizeLineEnds("this is a sentence\n");
    string actual = TestUtils.NormalizeLineEnds(_filePartReader.ReadLines());
    // Assert
    Assert.AreEqual(expected, actual);
}
```

#### What is TDD? What are the benefits?

WIP

**Test-driven development (TDD)** is a software development process that relies on the repetition of a very short development cycle:

1. requirements are turned into very specific test cases
2. then the code is created / improved so that the tests pass

Benefits:

- You get immediate feedback on if your code is working, so you can **find bugs faster**
- By seeing the test go from red to green, you know that you have both a working **regression test**, and working code
- You gain **confidence to refactor existing code**, which means you can clean up code without worrying what it might break
- At the end you have a suite of regression tests that can be run during automated builds to give you greater confidence that your codebase is solid

Other benefits:

- Better understanding of what you're going to write: When you write the test cases first, you think more critically about the _corner cases_. It's then easier to address them when you write the code and ensure that they're accurate.
- Enforces the policy of writing tests a little better
- Speeds up development in many cases

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

WIP

- Never push a failing test to the repository.
- Use **separate folder for tests** as you might not want to deliver (ie. give to the user) your test along with the production code.
- Give **descriptive names** to test methods so that you can see what fails easier
- Write tests for the error cases and corner cases.
- Check only a single thing in one test method (practically: use **1 assert per test method**)
- Use assert (or expected exception) in all of the test methods.
- Use the expected result as the first argument of an assert method: `Assert.AreEqual(expected, actual);`
- Use the AAA pattern

#### What is arrange/act/assert pattern?

WIP

A **Unit Test** tests a single **"Act"** in a program, typically a single method call on an object instance. **Arrange, Act, Assert (AAA)** organizes a unit test into three parts: _before, during and after the Act_.

**Arrange**: Everything up to, but not including, the method call of interest. We set up the **state** that we want the world (the object that we're calling the method on, other objects that it interacts with, etc.) to be in when we call the method.

**Act**: The call of the method we're testing.

**Assert**: The rest of the test, where we Assert that the Act had the effects on the world that we expect.

### DevOps

#### What is continuous integration? Why is CI important?

WIP

**Continuous Integration (CI)** is a **software development practice** (a fundamental DevOps best practice) where members of a team integrate (=merge to master in a Git workflow) their work frequently, usually each person integrates at least daily, leading to multiple integrations per day. Each integration is **verified by an automated build** (including test) to detect integration errors as quickly as possible.

A nicely working CI process needs the following:

- Good unit testing coverage.
- Automation: tests need to run with every commit/merge automatically.
- Ideally many kinds of tests: integration testing, UI testing, acceptance testing.

Developers practicing continuous integration merge their changes back to the main branch as often as possible. The developer's changes are validated by creating a build and running automated tests against the build. By doing so, you avoid integration challenges that can happen when waiting for release day to merge changes into the release branch.

Continuous integration puts a great emphasis on testing automation to check that the application is not broken whenever new commits are integrated into the main branch.

**What you need (cost)**:

- Your team will need to write automated tests for each new feature, improvement or bug fix.
- You need a continuous integration server that can monitor the main repository and run the tests automatically for every new commits pushed.
- Developers need to merge their changes as often as possible, at least once a day.

> One of the traditional cost associated with continuous integration is the installation and maintenance of a _CI server_. But you can reduce significantly the cost of adopting these practices by using a **cloud service** (like Bitbucket Pipelines which adds automation to every Bitbucket repository).

**What you gain**:

- Less bugs get shipped to production as regressions are captured early by the automated tests.
- Building the release is easy as all integration issues have been solved early.
- Less context switching as developers are alerted as soon as they break the build and can work on fixing it before they move to another task.
- Testing costs are reduced drastically – your CI server can run hundreds of tests in the matter of seconds.
- Your QA team spend less time testing and can focus on significant improvements to the quality culture.

Main benefits:

- No merge hell (a.k.a. integration hell)
- Testable build always available

> "If it hurts, do it often so it doesn't hurt so much!"

#### Why are tests important in the CI workflow?

WIP

These tests confirm that the newest code integrates with what's currently in the master branch.

#### Name some software that help the CI workflow!

- Azure Pipelines: a Microsoft product free for up to five users and open-source projects.
- Jenkins: a free, open-source, Java-based tool that gives you a lot of flexibility.
- Cloud Build: the managed service offering from Google Cloud Platform.
- Travis CI: a popular tool for GitHub open-source projects that offers a hosted or self-hosted solution.
- GitLab CI: a free tool from GitLab that can also integrate with other tools via the API.
- AWS CodePipeline
- Bitbucket Pipelines

#### What is Continuous Delivery?

WIP

**Continuous Delivery (CD)** is the ability to get changes of all types -- including new features, configuration changes, bug fixes and experiments -- into production, or into the hands of users, **safely** and **quickly** in a **sustainable** way.

The goal is to make deployments -- whether of a large-scale distributed system, a complex production environment, an embedded system, or an app -- **predictable**, routine affairs that can be performed **on demand**.

We achieve all this by ensuring our code is always in a deployable state, even in the face of teams of thousands of developers making changes on a daily basis.

Continuous delivery is an extension of continuous integration since it automatically deploys all code changes to a testing and/or production environment after the build stage.

This means that on top of _automated testing_, you have an **automated release** process and you can deploy your application any time by clicking a button.

> Make sure that you release small batches that are easy to troubleshoot in case of a problem -- deploy to production early and often.

**What you need (cost)**:

- You need a strong foundation in continuous integration and your test suite needs to cover enough of your codebase.
- Deployments need to be automated. The trigger is still manual but once a deployment is started there shouldn't be a need for human intervention.
- Your team will most likely need to embrace feature flags so that incomplete features do not affect customers in production.

**What you gain**:

- The complexity of deploying software has been taken away. Your team doesn't have to spend days preparing for a release anymore.
- You can release more often, thus accelerating the _feedback loop_ with your customers.
- There is much less pressure on decisions for small changes, hence encouraging iterating faster.

#### What is Continuous Deployment?

WIP

**Continuous Deployment (CD)** goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

Continuous deployment is an excellent way to accelerate the **feedback loop** with your customers and take pressure off the team as there isn't a _Release Day_ anymore. Developers can focus on building software, and they see their work go live minutes after they've finished working on it.

> Continuous deployment is like continuous delivery, except that **releases happen automatically**.

**What you need (cost)**:

- Your testing culture needs to be at its best. The quality of your test suite will determine the quality of your releases.
- Your documentation process will need to keep up with the pace of deployments.
- Feature flags become an inherent part of the process of releasing significant changes to make sure you can coordinate with other departments (Support, Marketing, PR...).

**What you gain**:

- You can develop faster as there's no need to pause development for releases. Deployment pipelines are triggered automatically for every change.
- Releases are less risky and easier to fix in case of problem as you deploy small batches of changes.
- Customers see a continuous stream of improvements, and quality increases every day, instead of every month, quarter or year.

#### What is DevOps?

WIP

**DevOps** is a set of practices that combines software development (_Dev_) and IT operations (_Ops_). It aims to **shorten the system's development life cycle** and provide **continuous delivery with high software quality**.

DevOps is a new practice and job role in Software development that emerged from the birth of the **cloud** and **agile** methodologies. It can be seen as an _evolution of the **SysAdmin** role_, but requires much more knowledge. Typical tasks of a DevOps person is everything IT related except actually writing the software. In practice this means the following:

- Build systems that enable **CI/CD** workflows
- Manage the **"cloud"**, set up its infrastructure, security, install and configure apps
- Make sure that there are **monitoring** and **alerting systems** in place in case of issues
- **Automate** everything: deployments, releases, upgrades.

Usually a good DevOps person needs the following knowledge:

- In-depth knowledge of **Linux** (since most software in the cloud runs on this platform)
- In-depth knowledge of at least one **cloud provider** (Amazon Web Services, MS Azure, Google Cloud, etc.)
- Good knowledge of **CI/CD workflows and software** that helps it (Jenkins, Travis, Docker, Kubernetes, Ansible, Chef, and many many more. This is a really new and rapidly changing landscape)
- Some knowledge of a **scripting language** (usually python or bash) and a little Maven/Gradle

DevOps automation can be achieved by repackaging platforms, systems, and applications into reusable building blocks through the use of technologies such as **virtual machines** and **containerization**.

> DevOps is often viewed as an approach to applying systems administration work to **cloud** technology.

> Although in principle it is possible to practice DevOps with any architectural style, the **microservices** architectural style is becoming the standard for building continuously deployed systems.

### Software Methodologies

#### What kind of software-lifecycle models do you know?

WIP

- Agile development
- Waterfall model

#### What is a UML diagram? What kind of diagram types do you know?

WIP

The **Unified Modeling Language** is a standard **visual modeling language** intended to be used for:

- Modeling business and similar processes,
- Analysis, design, and implementation of software-based systems

There are two major kinds of UML diagram, structure diagrams and behavior diagrams:

- **Structure diagrams**: show the **static structure** of the system and its parts on different abstraction and implementation levels and how they are related to each other. The elements in a structure diagram represent the meaningful concepts of a system, and may include abstract, real world and implementation concepts.
- **Behavior diagrams**: show the **dynamic behavior** of the objects in a system, which can be described as a series of changes to the system over time.

I've used **Class Diagrams** (structure) extensively, and **Sequence Diagrams** (behavior) occasionally.

> Draw.io > PlantUML

#### What is a UML class diagram? What are the typical elements?

WIP

Before implementating a bunch of classes, you'll want to have **a conceptual understanding of the system** — that is, what classes do I need? What functionality and information will these classes have? How do they interact with one another? Who can see these classes? And so on.

That's where class diagrams come in. Class diagrams are a neat way of visualizing the classes in your system before you actually start coding them up. They're **a static representation of your system structure**.

Why do we need class diagrams:

1. **Planning** and modeling ahead of time make programming much easier.
2. Besides that, **making changes** to class diagrams is **easy**, whereas coding differnent functionality after the fact is kind of annoying.
3. When someone wants to build a house, they don't just grab a hammer and get to work. They need to have a **blueprint** — a design plan — so they can ANALYZE & modify their system.
4. You don't need much technical/language-specific knowledge to **understand** it.

**UML Class Notation**:

A class is represented as a box with **3 compartments**. The uppermost one contains the **class name**. The middle one contains the **STATE = class attributes** and the last one contains the **BEHAVIOR = class operations** (methods).
Each attribute has a _type_. Each operation has a _signature_.

**Class visibility**:

- \- private
- \# protected
- ~ package
- \+ public

**Relationships**:

- **Association**:
  - Associations are relationships between classes in a UML Class Diagram. They are represented by **a solid line between classes**. Associations are typically named using a verb or verb phrase which reflects the real world problem domain.
  - General association is simply a solid line.
  - E.g. `Airplane -- Ticket`
- **Generalization (inheritance)**:
  - Represents an **"is-a" relationship**.
  - An abstract class name is shown in italics.
  - Represented by **a solid line + an empty arrow** pointing to the **extended** class.
  - E.g. `Square --|> Rectangle`
- **Realization**:
  - Same as Inheritence but with interfaces.
  - Interface is shown between two diamond operators + name in italics: `<<interface>> IMyInterface`
  - Represented by **a dashed line + an empty arrow** pointing to the **implemented** interface.
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
- **Structural**: designing objects to satisfy particular project constraints. These work with the way objects are connected with other objects to ensure that changes in the system don't require changes to those connections. E.g. **Decorator pattern**.
- **Behavioral**: designing objects that handle particular types of actions within a program. These encapsulate processes that you want to perform, such as interpreting a language, fulfilling a request, moving through a sequence (as in an iterator), or implementing an algorithm. E.g. Iterator pattern.

1. **Factory Method pattern** (creational):
   - A normal factory produces goods; a software factory produces objects. And not just that — it does so without specifying the exact class of the object to be created. To accomplish this, objects are created by calling a factory method instead of calling a constructor.
   - There's nothing wrong with using `new` to create objects but it comes with the baggage of **tightly coupling** our code to the concrete implementation class, which can occasionally be problematic.
   - **Static factory methods** returning the same type as the containing class are **substitutes for constructors**, with several advantages:
     - Unlike constructors, they have **names**. In some cases this makes our code **more readable**. More importantly, it is possible to have **two different factory methods with the same signature**.
     - Unlike constructors, they are **not required to create a new object** each time they're invoked. We can add features like pooling, caching, lazy loading, or other extras and limitations. Singleton's `getInstance()` is a good example for this.
     - Unlike constructors, they can **return an object of any subtype** of their return type.
2. **Singleton pattern** (creational):
   - The singleton pattern is used to limit creation of a class to only **one object**. This is beneficial when one (and only one) object is needed to coordinate actions across the system.
   - There are several examples of where only a single instance of a class should exist, including **caches**, **loggers**, etc.
3. **Iterator pattern** (behavioral):
   - The iterator pattern is a design pattern in which an iterator is used to **traverse a container** and access the container's elements. The iterator pattern **decouples algorithms from containers** in most cases.
   - For example, the hypothetical algorithm _SearchForElement_ can be implemented generally using a specified type of iterator rather than implementing it as a container-specific algorithm. This allows _SearchForElement_ to be used on any container that supports the required type of iterator.
   - `foreach`

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
   - _Open_ for **extension**, _Closed_ for **modification**
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

...

## Software design

### Security

#### What is OAuth2?

WIP

Meant for a service to **authorize** _another service_. (Not meant for _authentication_, as the user is authenticated with both services already).

OAuth access token:

- Contains user-allowed permissions
- Trustable (cannot be tampered)

> OAuth access tokens are JWTs (JSON Web Tokens).

#### What is Basic Authentication?

WIP

**HTTP** provides a general framework for access control and authentication called the "Basic" schema. It can be used by a server to _challenge_ a client request, and by a client to provide authentication information.

The challenge and response flow works like this:

1. If a request requires authentication, the server returns `401` (Unauthorized). The response includes a `WWW-Authenticate` header, indicating the server supports Basic authentication.
2. The client sends another request, with the client credentials in the `Authorization` header. The credentials are formatted as the string "name:password", base64-encoded. The credentials are not encrypted.

Because the credentials are sent unencrypted, Basic authentication is **only secure over HTTPS**.

Basic authentication is also **vulnerable to CSRF attacks**. After the user enters credentials, the browser automatically sends them on subsequent requests to the same domain, for the duration of the session. This includes AJAX requests.

Advantages:

- Internet standard.
- Supported by all major browsers.
- Relatively simple protocol.

Disadvantages:

- User credentials are sent in the request.
- Credentials are sent as plaintext.
- Credentials are sent with every request.
- No way to log out, except by ending the browser session.
- Vulnerable to cross-site request forgery (CSRF); requires anti-CSRF measures.

#### What is CORS, why it’s needed in browsers?

#### How can you initialize a CSRF attack?

WIP

**Cross-Site Request Forgery (CSRF)** is an attack where a malicious site sends a request to a vulnerable site where the user is currently logged in. It allows an attacker to partly **circumvent the same origin policy**, which is designed to prevent different websites from interfering with each other.

In a successful CSRF attack, the attacker causes the victim user to carry out an action unintentionally. For example, this might be to change the email address on their account, to change their password, or to make a funds transfer. Depending on the nature of the action, the attacker might be able to gain full control over the user's account. If the compromised user has a privileged role within the application, then the attacker might be able to take full control of all the application's data and functionality.

For a CSRF attack to be possible, three key conditions must be in place:

1. A relevant action. There is an action within the application that the attacker has a reason to induce. This might be a privileged action (such as modifying permissions for other users) or any action on user-specific data (such as changing the user's own password).
2. Cookie-based session handling. Performing the action involves issuing one or more HTTP requests, and the application relies solely on session cookies to identify the user who has made the requests. There is no other mechanism in place for tracking sessions or validating user requests. However, CSRF attacks are not limited to exploiting cookies. For example, Basic and Digest authentication are also vulnerable. (After a user logs in with Basic or Digest authentication. the browser automatically sends the credentials until the session ends).
3. No unpredictable request parameters. The requests that perform the action do not contain any parameters whose values the attacker cannot determine or guess. For example, when causing a user to change their password, the function is not vulnerable if an attacker needs to know the value of the existing password.

Typically, the attacker will place the malicious HTML onto a web site that they control, and then induce victims to visit that web site. This might be done by feeding the user a link to the web site, via an email or social media message. Or if the attack is placed into a popular web site (for example, in a user comment), they might just wait for users to visit the web site.

If a victim user visits the attacker's web page, the following will happen:

- The attacker's page will trigger an HTTP request to the vulnerable web site.
- If the user is logged in to the vulnerable web site, their browser will automatically include their session cookie in the request (assuming **SameSite** cookies are not being used).
- The vulnerable web site will process the request in the normal way, treat it as having been made by the victim user, and change their email address (or something similar).

A concrete example of a CSRF attack:

- The attacker sends an email with a beautiful offer, and adds a CTA button at the end, "GET A 50% DISCOUNT".
- The user is thrilled by this awesome offer and clicks the button.
- In reality, the button submits a POST form to your web application, and more specifically to the endpoint that changes the user's password with a new one.
- Because cookies are sent in every request, even cross-domain ones, the endpoint works as expected if the user has logged in, in an earlier step to your web application.
- Now the user is logged out and cannot log in to your web application anymore.

The most robust way to defend against CSRF attacks is to include a **CSRF token** within relevant requests. The token should be:

- Unpredictable with high entropy, as for session tokens in general.
- Tied to the user's session.
- Strictly validated in every case before the relevant action is executed.

#### What is JWT used for? Where to store it on client side?

WIP

A **JSON Web Token (JWT)** is an open standard that defines a compact and self-contained way for **securely transmitting information** between parties as a JSON object. This information can be verified and trusted because it is **digitally signed**. JWTs can be signed using a secret or a public/private key pair.

JWTs allow backend developers to authenticate users, without making a single query to the database server or any other type of storage.

Here are some scenarios where JSON Web Tokens are useful:

- **Authorization**: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.
- **Information Exchange**: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed -- for example, using public/private key pairs -- you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

JWTs are nothing more than a cryptographically signed, base64 representation of a JSON object. By signing the token, we make sure that its content was not altered in any way. This is achieved by verifying the received token with the exact same key that was used to sign it in the first place. In case the signature that we generate does not match the one in the token, we should consider that the token is invalid.

JWT tokens have three parts, all represented as base64 strings:

- The **header** typically consists of two parts:
  - the type of the token, which is JWT
  - the signing algorithm being used, such as HMAC SHA256 or RSA.
- The **payload**, which contains the _claims_. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims:
  - registered
  - public
  - private
- A **signature** created by signing the header and the payload

A JWT typically looks like this: `[header].[payload].[signature]`.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the `Authorization` header using the **Bearer** schema.

**Store JWTs securely**:

A JWT needs to be stored in a safe place inside the user's browser.

If you store it inside _localStorage_, it's accessible by any script inside your page (which is as bad as it sounds, as an _XSS attack_ can let an external attacker get access to the token).

**Don't store it in local storage (or session storage)**. If any of the third-party scripts you include in your page gets compromised, it can access all your users' tokens.

The JWT needs to be stored inside an **httpOnly cookie**, a special kind of cookie that's only sent in HTTP requests to the server, and it's never accessible (both for reading or writing) from JavaScript running in the browser.

> JWT is a great technology for API authentication and server-to-server authorization. It's not a good choice for sessions.

### Threaded programming

#### When do you need to use threads in an application?

WIP

#### What is a daemon thread?

#### What is the difference between concurrent and parallel execution of code?

#### What is the most important problem developers are faced when using threads?

#### In what kind of situations can deadlocks occur?

#### What are possible ways to prevent deadlocks from occurring?

#### What does critical section or critical region mean in the context of concurrent programming?
