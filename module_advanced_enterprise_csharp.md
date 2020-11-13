# Enterprise module (C# branch)

### ASP.NET Core, WCF

#### What Is the difference between .NET Core and .NET Standard? How do them relate to “classic” .NET?

WIP

**.NET Core**:

The .NET Framework is used for building desktop applications and ASP.NET applications running on Internet Information Server (IIS). It was the first managed framework released.

Xamarin is a managed framework used for building iOS, Android, and macOS desktop applications.

**.NET Core** is a free, cross-platform, open source implementation of the managed framework. It supports 4 types of applications:

- console
- ASP.NET Core
- cloud
- Universal Windows Platform (UWP)
- Windows Forms and Windows Presentation Foundation (WPF) are not part of .NET Core

(Technically, .NET Core only supports console applications. ASP.NET Core and UWP are application models built on top of .NET Core).

Unlike the .NET Framework, .NET Core is not considered a Windows component. Therefore, updates come as **NuGet packages**, not through Windows Update. Updated through the package manager, applications can be associated with a particular .NET Core version and be **updated individually**.

**.NET Standard**:

Each implementation of the managed framework has its own set of Base Class Libraries. The **Base Class Library (BCL)** contains classes such as exception handling, strings, XML, I/O, networking, and collections.

**.NET Standard is a specification for implementing the BCL**. Since a .NET implementation is required to follow this standard, application developers will not have to worry about different versions of the BCL for each managed framework implementation.

**Framework Class Libraries (FCL)** such as WPF, WCF, and ASP.NET are **_not_ part of the BCL**, and therefore are _not_ included in .NET Standard.

Conclusion:

.NET Standard is an **API specification** that defines, for a given version, what **Base Class Libraries** must be implemented.

.NET Core is a **managed framework** that is optimized for building console, cloud, ASP.NET Core, and UWP (Universal Windows Platform) applications. It provides **an implementation of .NET Standard for the _Base Class Libraries_**.

> ASP stands for Active Server Pages.

_**More .NET Core**_:

The .NET Core platform is made up of several components, including the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.

The main characteristics of .NET Core:

- **Cross-Platform**:
  You can write apps and libraries that run unmodified across supported operating systems (Windows, Linux, macOS)
- **Open source**:
  .NET Core is one of the many projects under the stewardship of the .NET Foundation and is available on GitHub. As an open-source project, .NET Core promotes a more transparent development process and an active and engaged community.
- **Flexible deployment**:
  There are 2 main ways to deploy your app:
  - Framework-dependent deployment:
    Only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.
  - Self-contained deployment:
    The .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side by side with other versions.
- **Modular**:
  Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller, feature-centric packages (**NuGet assembly packages**). This modularity enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.
  The benefits of a smaller app surface area include:
  - tighter security
  - reduced servicing
  - improved performance
  - decreased costs in a pay-for-what-you-use model

Benefits and features:

- Cross Platform
- Open-Source
- One programming model for MCV and Web API
- Dependency Injection
- Modularity:
  - ASP.NET provides modularity with **middleware components**
  - both the request and response pipelines are composed using middleware components

#### What is ASP.NET MVC?

WIP

**ASP.NET Core**:

ASP.NET Core is a cross-platform, high-performance, open-source framework for building modern, cloud-based, Internet-connected applications. ASP.NET Core is a redesign of ASP.NET 4.x, with architectural changes that result in a leaner, more modular framework. With ASP.NET Core, you can:

- Build web apps and services, IoT apps, and mobile backends
- Use your favorite development tools on Windows, macOS, and Linux
- Deploy to the cloud or on-premises
- Run on .NET Core or .NET Framework

Some of its benefits:

- Architected for testability.
- Razor Pages makes coding page-focused scenarios easier and more productive.
- Blazor lets you use C# in the browser alongside JavaScript. Share server-side and client-side app logic all written with .NET.
- Ability to develop and run on Windows, macOS, and Linux.
- Open-source and community-focused.
- Integration of modern, client-side frameworks and development workflows (React, Angular).
- Built-in **dependency injection** (IoC container).
- A lightweight, high-performance, and modular **HTTP request pipeline**.
- Ability to host on IIS as well as:
  - Kestrel
  - Apache
  - Docker
  - etc.

**ASP.NET Core MVC**:

ASP.NET Core MVC provides features to build web APIs and web apps:

- The **Model-View-Controller (MVC)** pattern helps make your web APIs and web apps testable.
- **Razor** markup provides a productive syntax for Razor Pages and MVC views.
- **Tag Helpers** enable server-side code to participate in creating and rendering HTML elements in Razor files.
- (Built-in support for multiple data formats and content negotiation lets your web APIs reach a broad range of clients, including browsers and mobile devices.)
- **Model binding** automatically maps data from HTTP requests to action method parameters.
- Model validation automatically performs client-side and server-side validation.

Both the MCV Controller and the ASP.NET Web API Controller class inherit from the same `Controller` base class and returns `IActionResult`.

- MVC: `ViewResult`
- API: `JsonResult`

#### Can you explain Model, Controller and View in MVC?

WIP

Application layers:

- User Interface Layer
- Business Logic Layer (Domain Layer)
- Data Access Layer

MVC is used for implementing the **UI Layer** of the application.

MVC is an architectural design pattern that consists of 3 fundamental parts:

- **Model**:
  - Set of classes that represent data + the logic to manage that data
- **View**:
  - Only contains logic to present the Model data (provided to the View by the Controller)
  - Like an HTML template
  - If it gets too complicated, you can use a _ViewModel_
- **Controller**:
  - Handles HTTP requests and responses
  - Routing rules map URLs to Controller **action methods**
  - Builds the Model when a corresponding request comes in

#### Explain the page lifecycle of MVC.

WIP

Whenever we request a URL the only thing happens is, an instance of a **Controller** is created and some **action method** of it is called which results in rendering the View as HTML as response in the browser.

1. Routing
2. URL Routing Module intercepts the Request
3. MVC Handler executes
4. Controller executes
5. Render View method call

#### What is Razor View Engine?

WIP

Razor View engine is a **templating engine** that uses a markup syntax that allows us to write **HTML** and server-side code in web pages using **C#** (or VB.NET).

Some of Razor Syntax Rules for C#:

- .cshtml extension
- Blocks must be always enclosed in `@{ ... }`
- Inline expressions (variables and functions) start with `@`
- Variables are declared with `var` keyword

#### What you mean by Routing in MVC?

There are 2 routing techniques:

- Conventional Routing
- Attribute Routing

The Controller handles the requests and responses. The incoming request URL is mapped to a Controller action method. This mapping is done by the Routing rules.

Conventional routing configures routing / URL mapping in the `Configure()` method in Startup.cs.

Attribute routing does URL mapping via attributes. They can be placed above the Controller class as well as the action methods:

- `[Route("api/[controller]")]`
- `[Route("Home/[action]/{id}")]`
- `[Route("Home/Details/{id?}")]`
- `[HttpPost("{city}")]`
- etc.

`http://localhost:1234/Home/Details/7` -> `HomeController` Controller class -> `Details(7)` Action Method with parameter

Attribute routes offer a bit more flexibility than conventional routes.

**Conventional routes** are used for Controllers that serve **HTML pages**, and **Attribute routes** for Controllers that serve **REST APIs**. However, there's nothing stopping us from mixing the two methods.

#### What is Layout in MVC?

Repetitive sections, such as header, footer, menu bar, etc. can be defined _once_ in a Layout View. Maintaining the same look and feel across all Views becomes much easier, as we have only 1 layout file to modify.

Conventionally shared in a 'Shared' folder. Can be added from a template in VS (Razor View Layout Page). Starts with an underscore. The default name is `_Layout.cshtml`. An application can have multiple Layout Views.

The View Layout page renders view specific content in the body with `@RenderBody()` method.

Individual Views need to import the Layout View like so:

```csharp
@{
    Layout = `~/Views/Shared/_Layout.cshtml`
}
```

#### What ConfigureServices() method does in Startup.cs?

WIP

**Startup.cs**:
ASP.NET Core apps use a _Startup_ class, which is named Startup by convention. The Startup class:

- Optionally includes a `ConfigureServices` method to configure the app's services. A service is a reusable component that provides app functionality. Services are _registered_ in `ConfigureServices` and consumed across the app via dependency injection (DI) or ApplicationServices.
- Includes a `Configure` method to create the app's request processing pipeline.

`ConfigureServices` and `Configure` are called by the ASP.NET Core runtime when the app starts.

**ConfigureServices**:
The `ConfigureServices` method is:

- Optional.
- Called by the host before the `Configure` method to configure the app's services.
- Where configuration options are set by convention.

Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on how the host was configured.
For features that require substantial setup, there are `Add{Service}` extension methods on `IServiceCollection`. For example, `AddDbContext`, `AddDefaultIdentity`, `AddEntityFrameworkStores`, and `AddRazorPages`.

Adding services to the service container makes them available within the app and in the `Configure` method. The services are resolved via dependency injection or from ApplicationServices.

This method is also where dependencies are _registered_ with the Dependency Injection Container. This container provides the service to controllers.

#### What Configure() method does in Startup.cs?

**Configure**:
The `Configure` method is used to specify how the app responds to HTTP requests. The **request pipeline** is configured by adding **middleware** components to an `IApplicationBuilder` instance.

Hosting creates an `IApplicationBuilder` and passes it directly to `Configure`. `IApplicationBuilder` is available to the `Configure` method (as parameter), but it isn't registered in the service container.

The ASP.NET Core templates configure the pipeline with support for:

- Developer Exception Page
- Exception handler
- HTTP Strict Transport Security (HSTS)
- HTTPS redirection
- Static files
- ASP.NET Core MVC and Razor Pages

Each _Use_ extension method adds one or more middleware components to the request pipeline. For instance, `UseStaticFiles` configures middleware to serve static files.

Each middleware component in the request pipeline is responsible for invoking the next component in the pipeline (or short-circuiting the chain, if appropriate).

#### What is wwwroot folder in ASP.NET Core?

WIP

The **web root** is the base path for public, static resource files, such as:

- Stylesheets (.css)
- JavaScript (.js)
- Images (.png, .jpg)

By default, static files are served only from the web root directory and its sub-directories. The web root path defaults to {content root}/wwwroot.

In Razor _.cshtml_ files, tilde-slash (`~/`) points to the web root. (A path beginning with `~/` is referred to as a _virtual path_).

#### What’s the usage of [InternalsVisibleTo] attribute? What are pros and cons of it?

#### Explain what is WCF?

#### Mention what is the endpoint in WCF and what are the three major points in WCF?

### Object Relational Mapping, Entity Framework

#### What is an ORM? What are benefits, when to use?

WIP

An ORM eliminates the need for most of the data access code that developers usually need to write.

**The _Object-Relational Impedance Mismatch_**:

- **Granularity**:
  - Sometimes you will have an object model which has more classes than the number of corresponding tables in the database (we says the object model is more granular than the relational model). Take for example the notion of an Address...
- **Subtypes (inheritance)**:
  - Inheritance is a natural paradigm in object-oriented programming languages. However, RDBMSs do not define anything similar on the whole (yes some databases do have subtype support but it is completely non-standardized)...
- **Identity**:
  - A RDBMS defines exactly one notion of "**sameness**": the _primary key_. Java, however, defines both object identity `a==b` and object equality `a.equals(b)`.
- **Associations**:
  - Associations are represented as **unidirectional references** in Object Oriented languages whereas RDBMSs use the notion of _foreign keys_. If you need bidirectional relationships in Java, you must define the association twice.
  - Likewise, you cannot determine the **multiplicity** of a relationship by looking at the object domain model.
- **Data navigation**:
  - The way you access data in Java is fundamentally different than the way you do it in a relational database. In Java, you navigate from one association to an other walking the object network.
  - This is not an efficient way of retrieving data from a relational database. You typically want to minimize the number of SQL queries and thus load several entities via JOINs and select the targeted entities before you start walking the object network.

An ORM "... takes care of boring stuff, but provides manholes so you can get down with the SQL when you have to."

> Use ORMs for domain model persistence (complex, stateful CRUD).
> Use SQL for relational model interaction (complex, stateless querying).

#### What is Entity Framework? What are the advantages, limitations?

WIP

**EF (Entity Framework) Core** is an **ORM (Object-Relational Mapper)**, Microsoft's official data access platform.

It's lightweight, extensible, open source, and it works cross platform.

#### What is lazy loading?

#### What is the difference between code first and DB first approach?

WIP

**DB first**:

Pros:

- If we have an already-existing Database in place, this will most likely be the way to go as it will spare us the need to recreate it.
- Risk of data loss will be kept to a minimum, because any change or update will be always performed on the Database.

Cons:

- Manually updating the Database can be tricky if we're dealing with clusters, multiple instances, or a number of development/testing/production environment, as we will have to manually keep them in sync instead than relying upon code-driven updates/migrations or autogenerated SQL scripts.
- We will have even less control over the autogenerated Model classes (and their source code) than using Model-First approach; it will require an extensive knowledge over EF conventions and standards, otherwise we'll often struggle to get what we want.

**Code first**:

Pros:

- No need for diagrams and visual tools whatsoever, which can be great for small-to-medium size projects as it will save us a lot of time.
- A fluent code API that allows the developer to follow a Convention over Configuration approach, to handle the most common scenarios, while also giving him the chance to switch to custom, attribute-based implementation overrides whenever he needs to customize the Database mapping.

Cons:

- A good knowledge of the ORM programming language and conventions – C# for Entity Framework – is required.
- Maintaining the Database can be tricky sometimes as well as handling updates without suffering data loss; the Entity Framework's migrations support greatly mitigates the problem, although it also affected the learning curve in a negative way.

**Summary**: As long as we're dealing with a rather small project – for example, a _microservice_ – and/or we're aiming for a _flexible, mutable small-scale data structure_, adopting the **Code-First approach** will almost always be a good choice.

#### What is a migration script?

#### What is a navigation property?

#### Name 3 different attributes used in EF Core, what can they do for you?
