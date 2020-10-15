# Enterprise module (C# branch)

### ASP.NET Core, WCF

#### What Is the difference between .NET Core and .NET Standard? How do them relate to “classic” .NET?

#### What is ASP.NET MVC?

#### Can you explain Model, Controller and View in MVC?

#### Explain the page lifecycle of MVC.

#### What is Razor View Engine?

#### What you mean by Routing in MVC?

#### What is Layout in MVC?

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

This method is also where dependencies are _registered_ with the Dependency Injection Container.

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

#### Object Relational Mapping, Entity Framework

#### What is an ORM? What are benefits, when to use?

#### What is Entity Framework? What are the advantages, limitations?

#### What is lazy loading?

#### What is the difference between code first and DB first approach?

#### What is a migration script?

#### What is a navigation property?

#### Name 3 different attributes used in EF Core, what can they do for you?
