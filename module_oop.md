# OOP questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?

The _fail-fast_ principle encourages us to **fail fast and early**: If an error occurs, fail immediately and visibly.
If something unusually or unexpectedly occurs, let the software fail immediately instead of postponing the failure or working around the failure. The longer it takes for a bug to appear on the surface, the longer it takes to fix and the greater it costs.

Fail-fast makes bugs and failures appear sooner, thus:

- Bugs are
  - earlier to detect,
  - easier to reproduce, and
  - faster to fix.
- It's faster to stabilize softwares.
- Fewer bugs and defects will go into production, thus leading to higher-quality and more production-ready software.
- The cost of failures and bugs are reduced.

## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?

Iterate through the list using 2 pointers. When the "fast" pointer reaches the end, the "slow" pointer will point to the middle element.

#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?

Loop over the array, and insert every element into a `HashSet` while checking the return value. If add() returns false, it means that element is not allowed in the Set, and that is your duplicate.

Complexity: O(n)

#### What is a linked list? How to find if a linked list has a loop?

`LinkedList` is a data structure consisting of a **group of nodes** which together represent a sequence. Each node is composed of **data** and a _link_ to the **next** node in the sequence.

The most notable difference between the `LinkedList` and the `ArrayList` is in the way they store objects.

The `ArrayList` is better for **storing** and **accessing** data, as it is very similar to a normal array.
The `LinkedList` is better for **manipulating** data, such as making numerous _inserts_ and _deletes_.

In addition to storing the object, the `LinkedList` stores the memory address (or link) of the element that follows it. It's called a linked list because each element contains a link to the neighboring element.

> Use an `ArrayList` when you need rapid access to your data OR if you want to add/remove items at the END of your list. "Use an ArrayList normally".
> Use a `LinkedList` when you need to make a large number of inserts and/or deletes.

#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?

WIP

**ArrayList**:

- add(): O(1)
- add(index, element): O(n)
- get(): O(1)
- indexOf(): O(n)
- contains(): O(n)

**LinkedList**:

- add(): O(1) at any position
- get(): O(n)
- remove(): O(1)
- contains(): O(n)

**HashMap**:

- containsKey(): O(1)
- get(): O(1)
- put(): O(1)
- remove(): O(1)

**Bubble Sort**: O(n^2)

**Quicksort**:

- Average: O(n log n)
- Worst case: O(n^2)

**Binary Search Tree**:

- Average: O(log n)
- Worst case: O(n)

#### How does HashMap work?

_Arrays_ and _Lists_ store elements as ordered collections, with each element given an integer index.

`HashMap` is used for storing data collections as key and value pairs. One object is used as a _key_ (index) to another object, the _value_.
The `put()`, `remove()`, and `get()` methods are used to _add_, _delete_, and _access_ values in the `HashMap`.

A `HashMap` cannot contain duplicate keys. Adding a new item with a key that already exists overwrites the old element.
The HashMap class provides `containsKey()` and `containsValue()` methods that determine the presence of a specified key or value.
If you try to get a value that is not present in your map, it returns the value of `null`.

//`null` is a special type that represents the absence of a value.//

#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)

If immutable, the object's **hashcode** won't change and it allows caching the hashcode of different keys which makes the overall retrieval process very fast.

Also for mutable objects, the hashcode might be dependent on fields that could change, if this happens you won't be able to find the key (and its value) in the HashMap since `hashCode()` returns different value.

### Other

#### What is a garbage collector, in a nutshell?

## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?

Assigning a value of one type to a variable of another type is known as _type casting_.

To cast a value to a specific type, place the type in parentheses and position it in front of the value:
`int a = (int) 3.14;`

Upcasting:
You can cast an instance of a subclass to its superclass (Java does it automatically):
`Animal a = new Cat();`

Downcasting:
Casting an object of a superclass to its subclass is called downcasting.

```java
Animal a = new Cat();
((Cat)a).makeSound();
```

#### Which order should we catch the exceptions? Why?

All catch blocks should be ordered from most specific to most general.
Following the specific exceptions, you can use the `Exception` type to handle all other exceptions as the last catch (although that's not always a good idea).

### Object-oriented

#### What is a class?

A class is a user defined **blueprint** or prototype from which objects are created. It represents the set of properties or methods that are common to all objects of one type.

#### What is an object?

It is a basic unit of Object Oriented Programming and **represents the real life entities**. A typical Java program creates many objects which interact by invoking methods.

An object consists of:

- **State**: It is represented by _attributes_ of an object. It also reflects the properties of an object.
- **Behavior**: It is represented by _methods_ of an object. It also reflects the response of an object with other objects.
- **Identity**: It gives a unique _name_ to an object and enables one object to interact with other objects.

//No object ever has the same _identity_ as another object; an object's identity is guaranteed unique within the memory of the running process.//

#### What is a constructor?

Constructors are special methods invoked when an object is created and are used to **initialize** them.
A constructor can be used to provide initial values for object attributes.

- A constructor name must be same as its class name.
- A constructor must have no explicit return type.

The constructor is called when you create an object using the `new` keyword.

//You can think of constructors as methods that will set up your class by default, so you don't need to repeat the same code every time.//

//Java automatically provides a default constructor, so all classes have a constructor, whether one is specifically defined or not.//

#### Do we require parameter for constructors?

Parameters are not required for constructors.

A single class can have multiple constructors with different numbers of parameters.

#### What is an interface?

An interface is a completely **abstract** class that contains only abstract methods.

Some specifications for interfaces:

- Defined using the `interface` keyword.
- May contain only `public static final` variables.
- Cannot contain a constructor because interfaces cannot be instantiated.
- Interfaces can extend other interfaces.
- A class can implement any number of interfaces.

Interfaces have the following properties:

- An interface is implicitly abstract. You do not need to use the `abstract` keyword while declaring an interface.
- Each method in an interface is also implicitly abstract, so the `abstract` keyword is not needed.
- Methods in an interface are implicitly `public`.

Use the `implements` keyword to use an interface with your class.
When you implement an interface, you need to override all of its methods.

//A class can inherit from just one superclass, but can implement multiple interfaces.//

Java 8 has added the concept of interface _default methods_ to Java interfaces. An interface default method can contain a default implementation of that method.
Classes that implement the interface but which contain no implementation for the default interface will then automatically get the default method implementation (and the code doesn't break).

You mark a method in an interface as a default method using the `default` keyword.

//Default methods can be overriden.//

//In some cases it can make sense to define constants in an interface, otherwise it's better to avoid variables/fields altogether.//

//Static methods in interfaces can be useful when you have some utility methods you would like to make available, which fit naturally into an interface related to the same responsibility. For instance, a `Vehicle` interface could have a `printVehicle(Vehicle v)` static method.//

#### What are access modifiers?

The access modifiers in Java specify the accessibility or scope of a _field_, _method_, _constructor_, or _class_. We can change the access level of fields, constructors, methods, and classes by applying the access modifier on them.

#### What is data hiding?

The idea behind **encapsulation** is to ensure that implementation details are not visible to users. The variables of one class will be _hidden_ from the other classes, accessible only through the methods of the current class. This is called **data hiding**.

To achieve encapsulation in Java, declare the class' variables as `private` and provide public setter and getter methods to modify and view the variables' values.

//Use setters only if you must.//

#### Can a static method use non-static members?

No. One of the basic rules of working with static methods is that you can't access a nonstatic method or field from a static method because the static method doesn't have an _instance_ of the class to use to reference instance methods or fields.

#### What is the difference between hiding a static method and overriding an instance method?

Overriding an instance method is based on _late binding_, whereas hiding a static method is based on _early binding_.

When you override a method, you still get the benefits of _run-time polymorphism_, and when you hide, you don't.

#### Define the following terms: Instantiation, Attribute, Method

Instantiation:
Creating a new instance of a class is called _instantiation_. The `new` keyword is used to instantiate a class object.

Attribute:
An _attribute_ is another term for a _field_. It's typically a public constant or a public variable that can be accessed directly.

Method:
A method is a block of code which only runs when it is called. Methods (also known as functions) are used to perform certain actions.

#### Could we access a static variable (or method) from a non-static method? Why?

Yes, instance methods can access class variables and class methods directly.

#### Could we access a non-static variable (or method) from a static method? Why?

No, class methods cannot access instance variables or instance methods directly — they must use an object reference. Also, class methods cannot use the `this` keyword as there is no _instance_ for `this` to refer to.

#### How many instances you have of a static variable of a given class?

Only one.

#### Why is it not a good practice to write a lot of static methods?

Our code may become too specific/rigid, which makes it hard to extend/maintain it.

//The question you have to ask before typing _static_ is the following: "If there were more instances of this class, would they _share_ this state/behaviour?" Don't use static unless the answer is "yes".//

//We cannot and should not think ahead of all the possible upgrades and specification changes. We have to find some golden mean when designing our classes between the too specific/rigid and the overgeneralized extremes. Try to write as flexible code as you can without putting in significant extra work for that! Use YAGNI!//

#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?

Class members represent states and behaviours connected to the _class_ itself — all of its instances at the same time.

Benefits:

- There's one version of them in memory, bound at compile-time (early binding).
- Depending on access level, class members can be reached from anywhere without needing an instance of the class.

When to use: see above

#### What is the ‘this’ reference?

Within an instance method or a constructor, `this` is a reference to the current object — the object whose method or constructor is being called. You can refer to any member of the current object from within an instance method or a constructor by using `this`.

The most common reason for using the `this` keyword is because a field is **shadowed** by a method or constructor parameter.

#### What are base class, subclass and superclass?

Tied with the concept of **inheritance**.

The class inheriting the properties of another is the **subclass** (also called _derived class_, or _child class_); the class whose properties are inherited is the **superclass** (_base class_, or _parent class_).

To inherit from a class, use the `extends` keyword.

The purpose of inheritance is twofold:

- to design a class structure in line with the real structure of the problem domain;
- to prevent code duplication: common parts of different classes (both variables and methods) should be written once and used through a common class.

#### Draw an object oriented family (as entities, with relations) on the whiteboard.

#### Difference between overloading and overriding?

**Early Binding** or Static Binding:

The binding that can be resolved at **compile time** is known as _static_ or _early binding_. The binding of `static`, `private` and `final` _methods_ happens at compile-time. The reason is that the these methods cannot be overridden and the type of the class is determined at the compile time. Method **overloading** is determined compile time.

**Late Binding** or Dynamic Binding:

The binding that can only be resolved at **run time** is known as _dynamic_ or _late binding_. Method **overriding** is a perfect example of dynamic binding as in overriding both parent and child classes have same method and in this case the type of the object determines which method is to be executed.

Differences:

- Static binding happens at _compile-time_ while dynamic binding happens at _runtime_.
- Binding of _private_, _static_ and _final_ methods always happen at compile time since these methods cannot be overridden.
- overriding => static binding
- overloading => dynamic binding

#### What are the Object Oriented Principles? Explain the concepts with realistic examples!

- **Encapsulation**:
  The packing of data and methods into a **single component**.

  - Control of the way data is accessed or modified
  - More flexible and easily changed code
  - Ability to change one part of the code without affecting other parts
    > When a variable is hidden by the `private` modifier and can be accessed only through a getter and/or setter, it is encapsulated.

- **Inheritance**:

  - Inheritance is the process that enables one class to acquire the properties (methods and variables) of another. With inheritance, the information is placed in a more manageable, **hierarchical order**.

- **Polymorphism**:

  - Polymorphism, which refers to the idea of "having many forms", occurs when there is a hierarchy of classes related to each other through inheritance.
  - A call to a member method will cause a **different implementation** to be executed, depending on the type of the object invoking the method.

- **Abstraction**:

  - Data abstraction provides the outside world with only essential information, in a process of representing **essential features** without including implementation details.
  - A good real-world example is a **book**. When you hear the term book, you don't know the exact specifics, such as the page count, the color, or the size, but you understand the idea, or _abstraction_, of a book.
  - The concept of abstraction is that we focus on essential qualities, rather than the specific characteristics of one particular example.
  - In Java, abstraction is achieved using **abstract classes** and **interfaces**.
  - An abstract class is defined using the `abstract` keyword.
  - If a class is declared abstract it cannot be instantiated (you cannot create objects of that type).
  - To use an abstract class, you have to inherit it from another class.
  - Any class that contains an _abstract method_ should be defined as abstract.

  An abstract method is a method that is declared without an implementation (without braces, and followed by a semicolon):
  `abstract void walk();`

  //Every Animal makes a sound, but each has a different way to do it. That's why we define an abstract class Animal, and leave the implementation of how they make sounds to the subclasses.
  This is used when there is no meaningful definition for the method in the superclass.//

  //An abstract class is a class that cannot be instantiated, meaning that you cannot create new instances of an abstract class. The sole purpose of an abstract class is to function as a base for other subclasses.//

#### What is method overloading?

Happens at **compile time**. A _subclass_ can define a behavior that's specific to the subclass type, meaning that a subclass can implement a superclass method based on its requirement.
When methods have the **same name**, but **different parameters**, this feature is known as _method **overloading**_, also known as **compile-time polymorphism**.

In order to overload a method, the argument lists of the methods must differ in either of these:

- number of parameters
- data type of parameters
- sequence of data type of parameters

If two methods have same name, same parameters and have different _return type_, then this is NOT a valid method overloading example - this will throw compilation error.

//Very useful for when you need the same method functionality for different types of parameters.//

#### What is method overriding?

Happens at **runtime**. A _subclass_ can define a behavior that's specific to the subclass type, meaning that a subclass can implement a superclass method based on its requirement.
When methods have the **same _signature_** (name + parameters) and **return type** This feature is known as _method **overriding**_, also known as **runtime polymorphism**, or _dynamic method dispatch_.

Rules for Method Overriding:

- Should have the same return type and arguments.
- The _overriding method's_ access level cannot be more restrictive than the _overridden method's_ access level.
- A method declared `private`, `static` or `final` (_non-virtual_) cannot be overridden. (However static methods can be re-declared in the subclass, in this case the subclass method would act differently and will have nothing to do with the same static method of superclass).
- If a method cannot be inherited, it cannot be overridden.
- Constructors cannot be overridden.
- The _overriding method_ (subclass) can throw unchecked exceptions, regardless of whether the _overridden method_ (superclass) throws any exceptions or not. However the overriding method (subclass) should not throw checked exceptions that are new or broader than the ones declared by the overridden method (superclass).
- If a class is extending an abstract class or implementing an interface then it has to override all the abstract methods unless the class itself is an abstract class.

The `@Override` annotation is used to make your code easier to understand, because it makes it more obvious when methods are overridden.
It also instructs the compiler: if you make any mistake such as wrong method name, wrong parameter types while overriding, you would get a compile time error.

#### Explain how object oriented languages attempt to simplify memory management for Programmers.

Automatic garbage collection surely helps.

_Garbage Collector_ is the program running in the background that looks into all the objects in the memory, and mark objects that are not referenced by any part of the program. All these unreferenced objects are then deleted and space is reclaimed for allocation to other objects.

One of the basic ways of garbage collection involves three steps:

1. **Marking**: This is the first step where garbage collector identifies which objects are in use and which ones are not in use.
2. **Normal Deletion**: Garbage Collector removes the unused objects and reclaim the free space to be allocated to other objects.
3. **Deletion with Compacting**: For better performance, after deleting unused objects, all the survived objects can be moved to be together. This will increase the performance of allocation of memory to newer objects.

> One of the best features of Java programming language is the automatic garbage collection, unlike other programming languages such as C or C++, where memory allocation and deallocation is a **manual process**.

#### Explain the “Single Responsibility” principle!

This principle states that a class should only have **one responsibility**. Furthermore, it should only have **one reason to change**.

Some of its benefits:

- **Lower coupling**: Less functionality in a single class will have fewer dependencies.
- **Testing**: A class with one responsibility will have far fewer test cases.
- **Organization**: Smaller, well-organized classes are easier to search than monolithic ones.

> Stands for 'S' in _SOLID_.

#### What is an object oriented program? Explain, show.

OOP is a programming methodology based on **objects**, instead of just functions and procedures.

Importance is given to **data** (properties of the object) rather than just writing instructions to complete a task.

An object is a **real-world problem** or idea that you want to **model** in your program. An object can represent anything, e.g. an employee, bank account, car, tortoise, etc.

#### How do you make a class immutable? What do you need to watch out for?

WIP

To create an immutable class in Java, you have to do the following steps:

1. Declare the class as `final` so it can't be extended.
2. Make all fields `private` so that direct access is not allowed.
3. Don't provide setter methods for variables.
4. Make all mutable fields `final` so that their value can be assigned only once.
   ...

//Immutable objects are instances whose state doesn't change after it has been initialized. For example, `String` is an immutable class and once instantiated its value never changes.//

#### How many instances can be created for an abstract class?

None.

Abstract classes cannot be instantiated. The purpose of an abstract class is to function as a base for subclasses.

## Programming languages

### Java

#### What is autoboxing and unboxing?

**Autoboxing** is the automatic conversion that the Java compiler makes between the **primitive type** and their corresponding **object wrapper classes**. For example, converting an `int` to an `Integer`.
If the conversion goes the other way, this is called **unboxing**.

For an autoboxing example, consider the following code:

```java
List<Integer> li = new ArrayList<>();
for (int i = 0; i < 50; i++)
    li.add(i);
```

The compiler does not generate an error because it creates an `Integer` object from `i` and adds the object to `li`. Thus, the compiler converts the previous code to the following at runtime:

```java
List<Integer> li = new ArrayList<>();
for (int i = 0; i < 50; i++)
    li.add(Integer.valueOf(i));
```

//Notice the complier uses `.valueOf()` in the background.//

#### If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?

- Java: The `short` type. 0-200 is well within the bounds of the 16 bits it uses.
- C#: The `byte` type. It represents an _unsigned_ byte in C#, which can store a whole number between 0-255.

#### What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?

General convention for a variable's scope is, it is accessible only within the block in which it is declared.

1. **Class variables**:
   A variable which is declared inside a class, outside all the blocks and is marked **static** is known as a class variable. The lifetime of a class variable is **until the end of the program** or as long as the class is loaded in memory.

2. **Instance variables**:
   A variable which is declared inside a class and **outside all the methods and blocks** is an instance variable. Lifetime of an instance variable is until the object stays in memory.

3. **Local variables**:
   All other variables which are not instance and class variables are treated as local variables including the parameters in a method. The lifetime of a local variable is until the control leaves the block in which it is declared.

#### What is the purpose of the ‘equals()’ method?

Each object has a predefined `equals()` method that is used for semantical equality testing.

To make it work for our classes, we need to override it and check the conditions we need.
There is a simple and fast way of generating the `equals()` method from within the IDE (so we don't have to write it manually).

#### What is the difference between '==' and 'equals()'?

When you compare objects using the equality testing operator (`==`), it actually compares the references and not the object values.

The `equals()` method is used for semantical equality testing.

#### What does the ‘static’ keyword mean?

When you declare a variable or a method as _static_, it belongs to the **class**, rather than to a specific _instance_. This means that only one _instance_ of a static member exists, even if you create multiple objects of the class, or if you don't create any. It will be shared by all objects.

Static fields are created and initialized when the class is first loaded. That happens when a static member of the class is referred to or when an instance of the class is created, whichever comes first.

> It's a common practice to use upper case when naming a static variable, although not mandatory.

#### Why is the main() method declared as static? Explain.

One of the basic rules of working with static methods is that you can't access a non-static method or field from a static method because the static method doesn't have an _instance_ of the class to use to reference instance methods or fields.

The best-known static method is **main**, which is called by the Java runtime to start an application. The main method must be _static_, which means that applications run in a static context by default.

In Java, to start a program is to call an existing `public static void main(String[] args)` method on a class. Let's reverse engineer this signature:

1. It must be `public` to be reachable from the outer world.
2. It must be `static` to be callable before creating any objects.
3. It is `void` since by design it does not return anything when the program ends normally.
4. It is possible to pass (multiple) arguments after the name of the class to the java runtime – these arguments are visible by the method through the `args` parameter.

#### What is the default access modifier in a class?

default (optional): The class is accessible only by classes in the same package. Also called _package-private_.

#### What is the JVM?

Stands for _Java Virtual Machine_.

The JVM has two primary functions:

- To allow Java programs to run on any device or operating system (known as the "Write once, run anywhere" principle),
- and to manage and optimize program memory.

//The JVM manages system memory and provides a portable execution environment for Java-based applications.//

#### What is the difference between the JRE and the JDK?

JRE:

- Stands for _Java Runtime Environment_.
- The JRE provides the minimum requirements for executing a Java application.
  It consists of
  - the _Java Virtual Machine_ (JVM), and
  - core classes and supporting files.

JDK:

- Stands for _Java Development Kit_.
- The JDK is a software development environment used for developing Java applications and applets.
- It includes the
  - Java Runtime Environment (JRE),
  - an interpreter/loader (java),
  - a compiler (javac),
  - an archiver (jar),
  - a documentation generator (javadoc),
  - and other tools needed in Java development.

JRE = JVM + Library Classes
JDK = JRE + Development Tools

#### What is the difference between long and Long?

`long`: (primitive)

- The `long` data type is a 64-bit signed Java primitive data type.
- It is used when the result of calculations on whole numbers may exceed the range of the int data type.
- Its range is -2^63 to 2^63 - 1.
- All whole numbers in the range of long are called integer literals of long type.
- An integer literal of type long always ends with 'L' (or lowercase 'l').

`Long`: (class)

- The `Long` Wrapper Class defines two constants to represent maximum and minimum values of long data type, `Long.MAX_VALUE` and `Long.MIN_VALUE`.

#### Can a long store bigger numbers than a Long?

No.

#### What kind of packages do you know under java.util.\* ? Bring at least 3 examples.

Contains the collections framework, legacy collection classes, event model, date and time facilities, internationalization, and miscellaneous utility classes (a string tokenizer, a random-number generator, and a bit array).

Packages are used to avoid name conflicts and to control access to classes.
A package can be defined as a group made up of similar types of classes, along with sub-packages.

Two major results occur when a class is placed in a package:

- First, the name of the package becomes a part of the name of the class.
- Second, the name of the package must match the directory structure where the corresponding class file resides.

#### What are the access modifiers in Java? Which one could we use for class?

Top level (classes):

- default (no modifier): The class is accessible only by classes in the same package. Also known as _package-private_.
- `public`: The class is accessible by any other class.

Member level (attributes and methods):

- `private`: Accessible only within the declared class itself.
- default (no modifier): A variable or method declared with no access control modifier is available to any other class in the same package.
- `protected`: Provides the same access as the _default_ access modifier, with the addition that subclasses can access _protected_ methods and variables of the superclass.
  //Makes the members visible (or "public") only to the subclasses//
- `public`: Accessible from any other class.

//It's a best practice to keep the variables within a class private. The variables are accessible and modified using getters and setters.//

#### Can an “enum” contain methods in Java? Explain.

No.

An `Enum` is a special type used to define collections of constants.
Basically, Enums define variables that represent members of a fixed set.

You should always use Enums when a variable (especially a method parameter) can only take one out of a small set of possible values.

If you use Enums instead of integers (or String codes), you increase compile-time checking and avoid errors from passing in invalid constants, and you document which values are legal to use.

//Month names, days of the week, deck of cards, etc.//

#### When would you use a private/protected/public attribute? What is the difference?

`private`:
When I want to achieve _encapsulation_/_data hiding_. Use `private` for your fields unless you have a good reason not to.

`protected`:
When I want to give access to subclasses outside the package.

`public`:
When I want to give access to all classes. It's safe to use `public` for your methods most of the time.

#### How do you prevent developers from subclassing a class?

Java: To prevent a class from being extended, it has to be declared with the `final` keyword.

C#: Declare the class with the `sealed` keyword.

#### How do you prevent developers from overriding a method in a subclass?

To prevent a method from being overridden in a subclass, it has to be declared with the `final` keyword. If we try to override a final method in a subclass, it will lead to an error during the compilation.

Another way is to simply declare the method as `private` (although there's a workaround for that).

#### How do you prevent developers from changing the value of a variable?

If you make any variable `final`, you cannot change its value. It will be a constant.

#### Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!

Java has `Currency` class that represents the ISO 4217 currency codes. `BigDecimal` is the best type for representing currency decimal values.

The disadvantage of `BigDecimal` is that it's slower, and it's a bit more difficult to program algorithms that way (due to basic arithmetic operations not being overloaded).
If you are dealing with money, or precision is a must, use `BigDecimal`. Otherwise `Double` tends to be good enough.

//Note: Never store money in a floating point format as they have imprecisions in their representation.//

//In C#, only `BigInteger` is supported, although the (128-bit) `Decimal` value type is appropriate for financial calculations that require large numbers of significant integral and fractional digits and no round-off errors.//

#### What happens if you try to call something, that you have no access to, because of data hiding?

It is illegal to access a variable declared private outside its class. The compiler throws an error.

#### What happens if you try to delete/drop an item from an array, while you are iterating over it?

The length of an array is fixed after creation, therefore it is not possible to remove any elements while iterating. However there is a method `removeElement()` in class `ArrayUtils`. This creates a new array without the element we want to remove. This uses iteration.

#### What happens if you try to delete/drop/add an item from a List, while you are iterating over it?

A `ConcurrentModificationException` occurs. You need an `Iterator` to do that.

#### What happens if you try to add an item to the end of an array, while you are iterating over it?

It is not possible, because arrays have a fixed size. If you want to add an element to the end of an array, you have to create a new array with length `myArray.length + 1`, copy the original list elements to the new one, and add your element to the end of the new array.

#### If you need to access the iterator variable after a for loop, how would you do it?

WIP

...

//An `Iterator` is an object that enables to cycle through a collection, obtain or remove elements. Before you can access a collection through an iterator, you must obtain one. Each of the collection classes provides an `iterator()` method that returns an iterator to the start of the collection. By using this iterator object, you can access each element in the collection, one element at a time.//

#### Which interfaces extend the Collection interface in Java. Which classes?

The _Java collections framework_ hierarchy consists of two distinct interface trees:

1. `Collection` interface
2. `Map` interface

The `Collection` interface provides the basic functionality used by all collections, such as _add_ and _remove_ methods. Its subinterfaces the `Set`, `List`, and `Queue`, provide for more specialized collections.

- The **`Set`** interface does not allow duplicate elements.
  e.g. `HashSet`

  - `SortedSet` is a subinterface of `Set` interface, that provides for ordering of elements in the set.
    e.g. `TreeSet`

- The **`List`** interface provides for an ordered collection, for situations in which you need precise control over where each element is inserted.
  e.g. `ArrayList`, `LinkedList`

- The **`Queue`** is a collection for holding elements prior to processing. Elements in a `Queue` are typically ordered in on a _FIFO_ (first-in-first-out) basis.
  e.g. `PriorityQueue`
  - The `Deque` is a subinterface of `Queue`, a double-ended-queue. The elements can be used in both _LIFO_ and _FIFO_.
    e.g. `ArrayDeque`, `LinkedList`

#### What is the connection between equals() and hashCode()? How are they used in HashMap?

When we put a value in the map, the key's `hashCode()` method is used to determine the **bucket** in which the value will be stored.

To retrieve the value, `HashMap` calculates the bucket in the same way – using `hashCode()`. Then it iterates through the objects found in that bucket and use the key's `equals()` method to find the exact match.

//Note that `hashCode()` and `equals()` need to be overridden only for classes that we want to use as map keys, not for classes that are only used as values in a map.//

//In most cases, we should use immutable keys.//

#### What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?

An `Exception` is an object that's created when an error occurs in a Java program, and Java can't automatically fix the error. The exception object contains information about the type of error that occurred.

The most important information — the cause of the error — is indicated by the name of the exception class used to create the exception. You usually don't have to do anything with an exception object other than figure out which one you have.

A **checked exception** is an exception that the compiler requires you to provide for it one way or another. If you don't, your program doesn't compile -- _checked when compiled_.

An **unchecked exception** is an exception that you can provide for, but you don't have to -- _checked at runtime_.

//ALL exceptions other than _runtime exceptions_ are known as _checked exceptions_.//

//`Object` <- `Throwable` <- `Exception` <- `RuntimeException` <- `IOException`, etc.//

#### What is Error in Java and how does it relate to Exception?

Exceptions are events that occur in the code. A programmer can handle such conditions and take necessary corrective actions.

Errors indicate that something severe enough has gone wrong, the application should crash rather than try to handle the error.

Both `Error` and `Exception` are subclasses of the `Throwable` class.

Errors belong to unchecked type and mostly occur at runtime.

e.g. `StackOverflowError`

#### When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?

The circumstances that prevent execution of the code in a finally block are:

- The death of a thread.
- Using of the `System.exit()` method.
- Due to an exception arising in the finally block.
  It always runs otherwise (even despite a `return` statement).

It's a good practice to use `close()` inside finally block. You can be sure that all input and output streams are closed properly regardless of whether the exception occurs or not.

It is the right place to close files, recover resources, and otherwise clean up after the code enclosed in the try block.

//It's a good practice to use a _try-with-resources_ statement for this instead.//

#### What is the largest number you can work with in Java?

`java.math.BigInteger`

In theory, `BigInteger` can grow as large as your RAM.

#### When you use method overriding, can you change the access level of the method, from protected to public? Why? When you use method overriding, can you change the access level of the method, from public to protected? Why?

Yes, and no.
You can broaden, but not narrow, the accessibility of an overriden method.

It's a fundamental principle in OOP: the child class is a fully-fledged instance of the parent class, and must therefore present _at least_ the same interface as the parent class. (Liskov substitution principle of SOLID)?

//SUPERCLASS access modifier <= SUBCLASS access modifier//

#### Can the main method be overridden? Explain your answer!

No. Because it's a static method, it can't be overriden (but it can be overloaded!).

//The best-known static method is main, which is called by the Java runtime to start an application. The main method must be static, which means that applications run in a static context by default.//

#### When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?

Yes. See below.

#### When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?

Unchecked exceptions: Yes.

Checked exceptions: The overriding method must NOT throw checked exceptions that are new or broader than those declared by the overridden method.
For example, a method that declares a `FileNotFoundException` cannot be overridden by a method that declares a `SQLException`, `Exception`, or any other non-runtime exception unless it's a subclass of FileNotFoundException.

#### What does "final" mean in case of a variable, method or a class?

Use the `final` keyword to mark a _variable_ constant, so that it can be assigned only once.

_Methods_ and _classes_ can also be marked final.

- methods: can't be overridden
- classes: can't be subclassed

#### What is the super keyword?

You can access the _superclass_ from the subclass using the `super` keyword.
For example, `super.var` accesses the `var` member of the superclass.

The `super` keyword is similar to `this` keyword. It is mainly used to:

- differentiate the members of superclass from the members of subclass, if they have same names
- invoke the superclass constructor from subclass

#### What are “generics”? When to use? Show examples.

In a nutshell, generics enable _types_ (classes and interfaces) to be parameters when defining classes, interfaces and methods.

Abstract types declared between angle brackets (`<>`) (a.k.a. _diamond operator_) can be used as **wildcards**.

Code that uses generics has many benefits over non-generic code:

- **Stronger type checks at compile time**.
  A Java compiler applies strong type checking to generic code and issues errors if the code violates **type safety**. Fixing compile-time errors is easier than fixing runtime errors.
- **Elimination of casts**, which results **cleaner code** and **better performance**.
- Enabling programmers to implement **generic algorithms**.
  By using generics, programmers can implement generic algorithms that work on collections of different types, can be customized, and are type safe and easier to read.

Bounded type parameters:
There may be times when you'll want to restrict the kinds of types that are allowed to be passed to a type parameter. For example, a method that operates on numbers might only want to accept instances of `Number` or its subclasses. This is what _bounded type parameters_ are for.
To declare a bounded type parameter, list the type parameter's name, followed by the `extends` keyword, followed by its upper bound.
`public static <T extends Comparable<T>> T maximum(T x, T y, T z) {...}`

#### What is the benefit of having “generic” containers?

See above.

#### Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?

In a nutshell: There are multiple choices, the optimal solution depends on what kind of data is to be transferred.

If data is String: most simple: System.out/System.in + ProcessBuilder; For low number of processes(<10): Through Sockets; For large number of processes: JMS; If data can be even Objects as well: Less processes: RMI; More processes: JMS; +Http

#### What is an annotation? What can be annotated and how? Show examples.

Annotations, a form of **metadata**, provide data about a program that is not part of the program itself. Annotations have no direct effect on the operation of the code they annotate.

Annotations have a number of uses, among them:

- Instructions to the compiler:
  There are three built-in annotations available in Java (`@Deprecated`, `@Override` & `@SuppressWarnings`) that can be used for giving certain instructions to the compiler.
- Compile-time instructors:
  Annotations can provide compile-time instructions to the compiler that can be further used by software build tools for generating code, XML files etc.
- Runtime instructions:
  We can define annotations to be available at runtime which we can access using java reflection and can be used to give instructions to the program at runtime.

### C&#35;

Java - C#
JDK - .NET SDKs
JRE - .NET
JVM - CLR
bytecode - IL / MSIL
Project - Solution
Package - Namespace
Annotation - Attribute
POJO - POCO
Maven - NuGet and dotnet CLI
Tomcat / Jetty - IIS
Spring Framework - ASP.NET
Stream API - LINQ
JUnit - NUnit
Mockito - Moq / (NSubstitute)
Functional interfaces ~ Delegates

#### Explain the purpose of IL and how does it relate to CLR?

WIP

A product of compilation of code written in high-level .NET languages. Once you compile your code written in one of these languages, you will get a binary that is made out of **IL (Intermediate Language)**. It is important to note that the IL is independent from any specific language that runs on top of the runtime.

When we run the executable, the _Just-In-Time (JIT)_ compiler of CLR compiles the IL in native machine code which is specific to the underlying architecture.

#### What does “managed code” mean?

WIP

When the C# program is executed, the _assembly_ is loaded into the CLR, which might take various actions based on the information in the manifest. Then, if the security requirements are met, the CLR performs just in time (JIT) compilation to convert the IL code to native machine instructions.

Code that is executed by the **CLR (Common Language Runtime)** is sometimes referred to as **managed code**, in contrast to "unmanaged code" which is compiled into native machine language that targets a specific system.

> To put it very simply, managed code is just that: **code whose execution is managed by a _runtime_**. In this case, the runtime in question is called the CLR, regardless of the implementation. CLR is in charge of taking the managed code, compiling it into machine code and then executing it. On top of that, runtime provides several important services such as automatic memory management (**garbage collector**), security boundaries, **type safety** etc.

Managed code is written in one of the high-level languages that can be run on top of .NET, such as C#, Visual Basic, F# and others. When you compile code written in those languages with their respective compiler, you don't get machine code. You get **IL (Intermediate Language)** code which the runtime then compiles and executes. (C++ is the one exception to this rule, as it can also produce native, unmanaged binaries that run on Windows).

> IL = CIL = MSIL

> **Managed code** is executed by the **managed runtime environment (CLR)**, whereas **unmanaged code** is executed directly by the **operating system**. Applications written in these languages (Java, C#, VB.Net, etc.) are always _aimed at runtime environment services_ to manage the execution. The code written in these types of languages are known as managed code.

#### What is an assembly?

WIP

Source code written in C# is compiled into an intermediate language (IL) that conforms to the CLI (command-line interface) specification. The IL code and resources (such as bitmaps and strings) are stored on disk in an **executable file** called an **assembly**, typically with an extension of **.exe** or **.dll**. An assembly contains a _manifest_ that provides information about the assembly's types, version, culture, and security requirements.

Once you produce IL from your high-level code, you will most likely want to run it. This is where the CLR takes over and starts the process of _Just-In-Time compiling_, or _JIT-ing_ your code from IL to machine code that can actually be run on a CPU. In this way, the CLR knows exactly what your code is doing and can effectively manage it.

> Assembly is similar to Library in Java.

#### What is the difference between an EXE and a DLL?

WIP

**EXE**:

- An **executable file**. It's an application by itself rather than a supportive file.
- Can be run individually as it contains an **entry point** (main function).

**DLL (Dynamic-Link Library)**:

- Used as a **supportive file** to other applications.
- The Library Functions are **linked** to the application at runtime **dynamically** (hence the name).
- A DLL can't be run by itself as it doesn't contain an entry point.

A dynamic-link library (DLL) is a module that contains functions and data that can be used by another module (application or DLL).

DLLs provide a way to modularize applications so that their functionality can be updated and reused more easily. DLLs also help reduce memory overhead when several applications use the same functionality at the same time.

#### What is strong-typing versus weak-typing? Which is preferred? Why?

WIP

**Strong typing** means that the type check is done at **compile time** and **weak typing** means that the type check is done at **run time**. .NET languages incorporate strong typing.

Basic rules for strong-typing:

- All variables (or data types) are known at compile time.
- There is strict enforcement of typing rules (a String can't be used where an Integer would be expected).
- All exceptions to typing rules results in a compile time error.

For robust applications, strong-typing is much preferred, whereas small scripts / programs benefit from weak-typing.

#### What is a namespace?

WIP

C# uses the concept of _namespaces_ to group logically related classes through the `namespace` keyword. These act similarly to _Java packages_, and a class with the same name might appear within two different namespaces. To access classes defined in a namespace external to the current one, use the `using` directive followed by the namespace name.

#### Explain sealed class in C#?

WIP

A class with the `sealed` modifier on its class declaration is the opposite of an abstract class: it **cannot be inherited**. You can mark a class as sealed to prevent other classes from overriding its functionality. Naturally, a sealed class cannot be abstract. Also note that _a struct is implicitly sealed_; therefore, it cannot be inherited.

> The sealed modifier is equivalent to marking a class with the final keyword in Java.

#### What is explicit vs. implicit conversion? Give examples of both of them.

WIP

**Implicit conversions**:
No special syntax is required because the conversion always succeeds and no data will be lost.
E.g.:

- smaller to larger integral types
- derived classes to base classes

**Explicit conversions (casts)**:
Require a **cast expression**. Casting is required _when information might be lost_ in the conversion, or when the conversion might not succeed for other reasons.
E.g.:

- numeric conversion to a type that has less precision or a smaller range
- base-class instance to a derived class

#### Is a struct stored on the heap or stack?

WIP

Normally, structs are stored on the **stack**.

A struct in C# is referred to as a **value type**. Variables of this type are not pointers, but the objects themselves. If you create a struct as a function-local variable, its memory will be allocated on the stack.

> If the struct instance is a class member, its memory will be allocated contiguously as part of the class instance's memory on the heap.

#### Can a struct have methods?

WIP

Although structs can contain constructors, constants, fields, methods, properties, indexers, operators, and nested types, they are mostly used simply to **encapsulate groups of related fields**.

Because structs are value types, they can be allocated slightly more efficiently than classes.

Structs differ from classes in that they cannot be abstract and do not support implementation inheritance (implicitly `sealed`).

Typically, you use structure types to design small data-centric types that provide little or no behavior (e.g. coordinates).

Because structure types have value semantics, it's recommended to define _immutable_ (`readonly`) structure types.

```csharp
public readonly struct Coords
{
    public Coords(double x, double y)
    {
        X = x;
        Y = y;
    }

    public double X { get; init; }
    public double Y { get; init; }

    public override string ToString() => $"({X}, {Y})";
}
```

> You can think of a struct as a lightweight class.

#### Can DateTimes be null?

WIP

No.

`DateTime` is a value type, which, just like int and double, has no meaningful `null` value.

`default(DateTime)` defaults to `DateTime.MinValue` (0001-01-01 00:00:00 -- depending on culture)

#### List out the differences between Array and ArrayList in C#?

WIP

The comparison is made between `Array` and `List<T>` since `ArrayList` is more or less deprecated.

Namespace:

- Arrays belong to `System.Array`
- Lists belong to `System.Collections.Generic.List`
- (`ArrayLists` belong to `System.Collections`)

Memory:

- Arrays have fixed size
- Lists can increase or decrease size dynamically

If you know the data is fixed length, and you want to micro-optimise for some very specific reason (after benchmarking), then an `Array` may be useful.
Otherwise use a `List<T>` in almost all other cases.

#### How is the using() pattern useful? What is IDisposable? How does it support deterministic finalization?

WIP

The `using` statement provides a convenient syntax that ensures the correct use of `IDisposable` objects. It works the same as the try/finally block, but it's shorter.

It supports deterministic finalization by automatically calling the `Dispose()` (e.g. `Close()`) method on the disposable resource once the control reaches the end of the using block.

#### How can you make sure that objects using dedicated resources (database connection, files, hardware, OS handle, etc.) are released as early as possible?

WIP

Instantiating the object in the `using` statement is usually the best way to go.

#### Why to use keyword “const” in C#? Give an example.

WIP

Both Java and C# provide the ability to declare a variable whose value is specified at compile time and cannot be changed at runtime.

Java uses the _final_ field modifier to declare such a variable, while C# uses the `const` keyword.

#### What is the difference between “const” and “readonly” variables in C#?

WIP

In addition to `const`, C# provides the `readonly` keyword to declare variables that can be assigned a value once at runtime--either in the **declaration statement** or else in the **constructor**. After initialization, the value of a readonly variable cannot change.

One scenario in which readonly variables are useful is when modules that have been compiled separately need to share data such as a version number. If module A is updated and recompiled with a new version number, module B can be initialized with that new constant value without having to be recompiled.

- `const`: compile-time
- `readonly`: run time

> If a readonly modifier is applied to a static field, it should be initialized in the static constructor of the class.

#### What is a property in C#?

WIP

In C#, a property is a named member of a _class_, _struct_, or _interface_ offering a neat way to access **private** fields through what are called the `get` and `set` accessor methods. The `value` keyword represents the value of a property.

If a property only has a get accessor, it is a _read-only_ property. If it only has a set accessor, it is a _write-only_ property. If it has both, it is a _read-write_ property.

> Internally, C# properties are special methods called accessors.

#### List out two different types of errors in C#?

WIP

`Exception` class is the base class of the `SystemException` and `ApplicationException` classes.

The `SystemException` class is the base class for all the exceptions that can occur during the execution of the program.

The `ApplicationException` class should be derive to create your own **custom exception class**.

Some `SystemException` examples:

- `ArgumentException`
- `DivideByZeroException`
- `IndexOutOfRangeException`
- `KeyNotFoundException`
- `StackOverflowException`

#### What is the difference between “out” and “ref” parameters in C#?

WIP

In C#, to **pass a value type by reference**, you need to specify one of the keywords `ref` or `out`.

The **difference** between these two keywords is in the **parameter initialization**. A `ref` parameter must be initialized before use, while an `out` parameter does not have to be explicitly initialized before being passed and any previous value is ignored.

Any method using an `out` parameter MUST set its value when called.

Stick with `out` unless you need `ref`.

> Also, `ref` and `out` are not just for value types. They also let you reset the object that a reference type is referencing from within a method.

#### Can we override private virtual method in C#?

WIP

No. The CLR doesn't allow to declare a private virtual method.

#### What's the difference between IEquatable and just overriding Object.Equals()?

WIP

`IEquatable<T>` lets a structure implement a **strongly typed** `Equals()` method so **no boxing** is required. Thus much **better performance** when using **value types** with generic collections.

#### Explain the differences between public, protected, private and internal. Explain access modifier – “protected internal” in C#!

WIP

C# modifiers are quite similar to those in Java, with several small differences. Each member of a class, or the class itself, can be declared with an access modifier to define the scope of permitted access. Classes that are not declared inside other classes can only specify the **public or internal** modifiers. Nested classes, like other **class members**, can specify any of the following five access modifiers:

1. `private`:
   - Visible only within the **given class**.
   - Equivalent to Java's _private_.
   - Default for class and struct members, and _nested_ classes, structs and delegates.
2. `protected`:
   - Visible from **derived classes**.
   - No Java equivalents.
   - No defaults.
3. `internal`:
   - Visible from the **same assembly**.
   - Equivalent to Java's _default / no modifier / "package-private"_
   - Default for _top-level_ classes, structs, interfaces, enums, and delegates.
4. `protected internal`:
   - Visible from the **same assembly** and **derived classes**.
   - Equivalent to Java's _protected_
   - No defaults.
5. `public`:
   - Visible to **all** (even other programs).
   - Equivalent to Java's _public_
   - Default for interface _members_, enum _members_, and property accessor / mutator _methods_.

|                      | Containing Classes | Derived Classes | Containing Assembly | Anywhere outside | Java equivalent |
| -------------------- | :----------------: | :-------------: | :-----------------: | :--------------: | :-------------: |
| `private`            |        Yes         |       No        |         No          |        No        |    _private_    |
| `protected`          |        Yes         |       Yes       |         No          |        No        |        -        |
| `internal`           |        Yes         |       No        |         Yes         |        No        |     default     |
| `protected internal` |        Yes         |       Yes       |         Yes         |        No        |   _protected_   |
| `public`             |        Yes         |       Yes       |         Yes         |       Yes        |    _public_     |

> In C#, the default access modifier for class members is `private`, while in Java, access defaults to anywhere from within the containing package!

#### What’s the difference between using `override` and `new` keywords when defining method in child class?

WIP

**Override**:

The `override` modifier **extends** the base class `virtual` method.

**New**:

The `new` modifier **hides** an accessible base class method.

#### Explain StringBuilder class in C#!

WIP

Just like in Java, C# developers should not use the string type for concatenating strings to avoid the overhead of creating new string classes every time the string is concatenated. Instead, developers can use the `StringBuilder` class, which is functionally equivalent to the Java StringBuffer class.

`StringBuilder` maintains a **mutable array** that is hoped to be larger than the final string, and stuffs new things into the array as necessary.

The old version used the maintain a dynamic array. The new implementation maintains a **_linked list_ of relatively small arrays**, and appends a new array onto the end of the list when the old one gets full.

> Using a `StringBuilder` is best practice: it's a lot more efficient than copying strings over and over.

#### How we can sort the array elements in descending order in C#?

WIP

`System.Array.Sort(myArray);`
`System.Array.Reverse(myArray);`

#### Can you use a value type as a generic type argument in C#? For example when implementing an interface like (IEquatable).

WIP

Yes. (See above).

#### What are Nullable Types in C#?

WIP

A nullable value type `T?` represents all values of its underlying value type `T` and an additional `null` value.

Any nullable value type is an instance of the generic `System.Nullable<T>` structure. You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.

You typically use a nullable value type when you need to represent the undefined value of an underlying value type. For example, a Boolean, or `bool`, variable can only be either `true` or `false`. However, in some applications a variable value can be undefined or missing. _**For example, a database field**_ may contain `true` or `false`, or it may contain no value at all, that is, `NULL`. You can use the `bool?` type in that scenario.

Use the null-coalescing (`??`) operator to assign a nullable type to a non-nullable type.

You always can use the following read-only properties to examine and get a value of a nullable value type variable:

- `Nullable<T>.HasValue` indicates whether an instance of a nullable value type has a value of its underlying type.
- `Nullable<T>.Value` gets the value of an underlying type if `HasValue` is `true`. If `HasValue` is `false`, the `Value` property throws an `InvalidOperationException`.

> Nullable types in C# are similar to Optionals in Java.

#### Conceptually, what is the difference between early-binding and late-binding?

WIP

In late binding, the compiler does not know about what kind of object it is and what are the methods or properties it holds, here the objects are dynamic objects. The type of the object is decided on the basis of the data it holds on the right-hand side during **run-time**.

Basically, late binding is achieved by using `virtual` methods. **Late binding is slower than early binding** because it requires lookups at run-time.

**Early Binding (Static Binding)**:

The binding that can be resolved at **compile time** is known as _static_ or _early binding_. The binding of `static`, `private`, and _non-virtual_ methods happens at compile-time. The reason is that the these method cannot be overridden and the type of the class is determined at the compile time. Method **overloading** is determined compile time.

**Late Binding (Dynamic Binding)**:

The binding that can only be resolved at **run time** is known as _dynamic_ or _late binding_. Method **overriding** is a perfect example of dynamic binding as in overriding both parent and child classes have same method and in this case the type of the object determines which method is to be executed.

**Differences**:

- Static binding happens at _compile-time_ while dynamic binding happens at _runtime_.
- Binding of _private_, _static_ and _non-virtual_ methods always happen at compile time since these methods cannot be overridden.

> overriding => early binding
> overloading => late binding

#### What is delegate, event, callback, multicast delegate?

WIP

**Delegate**:

**A delegate is a type safe function _pointer_.**

- Delegates are used to pass **methods as arguments** to other methods.
- A **`delegate` is a _type_** (class) that represents references to methods with a particular parameter list and return type. When you instantiate a delegate, you can associate its instance with **any method with a compatible _signature_ and _return type_**. You can invoke (call) the method through the **delegate instance**.
- Both **anonymous methods** and **lambda expressions** (in certain contexts) are **compiled to delegate types**.
- There are 3 types of delegates:

  1. **Single delegate**:
     - Used to invoke a single method.
  2. **Multicast delegate**:
     - Used to invoke multiple methods. The delegate instance can do multicasting (adding a new method on existing delegate instance). `+` and `–` operators can be used to add or remove a method from a delegate instance. All **methods will invoke in sequence** as they are assigned.
     - Basically a delegate that has **references to more than one method**
  3. **Generic delegate**:
     - Generic delegates don't require to _define_ the delegate instance in order to invoke the methods.
     - There are 3 types of generic delegates:
       - **Function**:
         `Func<T, TResult>` etc. encapsulates a method that has _0 or more parameters_ (1 in this case) and _**returns** a value of `TResult`_
       - **Action**:
         `Action<T>` etc. encapsulates a method that has _0 or more parameters_ (1 in this case) and _does **not** return a value_.
       - **Predicate**:
         `Predicate<T>` represents the method that defines a set of criteria and determines whether the specified object meets those criteria. `T` is the type of the object to compare. _It **returns** a Boolean (`true` or `false`)_.

**Event**:

Events enable a class or object to **notify** other classes or objects **when something of interest occurs**.

The class that **_raises_** (sends) the event is called the **publisher** and the classes that **_handle_** (receive) the event are called **subscribers**.

> A **publisher** is like a _button element_ or a _timer object_.
> A **subscriber** is like an _event handler_ (e.g. onclick).

Events have the following properties:

- The **publisher** determines **_when_** an event is **raised**.
- The **subscribers** determine **_what action is taken_** in response to the event.
- An _event_ can have **multiple subscribers**. A _subscriber_ can handle **multiple events** (from multiple publishers).
- Events that have no subscribers are never raised.
- Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.
- When an event has **multiple subscribers**, the event handlers are invoked **synchronously** when an event is raised. (Events can also be invoked **asynchronously**).
- In the .NET class library, events are based on the `EventHandler` delegate and the `EventArgs` base class.

**Callback**:

In computer programming, a callback is executable code that is passed as an argument to other code.
C# has **delegates** for that purpose. They are heavily **used with events**, as an event can automatically invoke a number of attached delegates (event handlers).

> **Event handlers** are nothing more than methods that are **invoked through _delegates_**.

#### What is enum in C#?

WIP

Enumerations, or enums, are used to **group named constants**. In C#, enums are **value types**, and enum constants must be integral numeric values. The `ToString()` method can be used to print out _string representations_ of the _named constants_.

```csharp
public enum Color
{
    Green,   //defaults to 0
    Orange,  //defaults to 1
    Red,     //defaults to 2
    Blue     //defaults to 3
}
```

#### What is null-conditional operator?

WIP

A **null-conditional operator** applies a member access, **`?.`**, or element access, **`?[]`**, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.

- If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.
- If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.

#### What is null-coalescing operator?

WIP

The **null-coalescing operator** **`??`** returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.

```csharp
int? a = null;
int b = a ?? -1;

Console.WriteLine(b);  // output: -1
```

The **null-coalescing assignment operator** **`??=`** assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.

```csharp
List<int> numbers = null;
(numbers ??= new List<int>()).Add(5);

Console.WriteLine(numbers[0]);  // output: 5
```

#### What is serialization?

WIP

Serialization is the process of **converting an object into a stream of bytes** to **store** the object or **transmit** it to _memory_, a _database_, or a _file_. Its main purpose is to **save the state of an object** in order to be able to **recreate it** when needed. The reverse process is called deserialization.

**Binary serialization**:

- Uses **binary encoding** to produce compact serialization for uses such as storage or socket-based network streams. In binary serialization, all members, even members that are read-only, are serialized, and performance is enhanced.
- Using the `BinaryFormatter` (`System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`) class. According to Microsoft, it's not safe to use anymore.

**JSON serialization**:

- Serializes the **public properties** of an object into a string, byte array, or stream (that conforms to the RFC 8259 JSON specification).
- Using the `JsonSerializer` (`System.Text.Json.JsonSerializer`) class.

**XML serialization**:

- Serializes the **public fields and properties** of an object, or the parameters and return values of methods, into an XML stream.
- Results in **strongly typed classes** with public properties and fields that are converted to XML.
- Using the `XmlSerializer` (`System.Xml.Serialization.XmlSerializer`) class.

#### What is the difference between Finalize() and Dispose() methods?

WIP

The **garbage collector (GC)** plays the main role in .NET for **memory _management_**.

**Managed resources** basically means "managed memory" that is managed by the garbage collector. When you no longer have any references to a managed object (which uses managed memory), the garbage collector will (eventually) release that memory for you.

**Unmanaged resources** are then everything that the _garbage collector does not know about_. For example:

- Open files
- Open network / DB connections
- Unmanaged memory

Normally you want to release those unmanaged resources before you lose all the _references_ you have to the object managing them. You do this by calling `Dispose()` on that object, or using the `using` statement which will handle calling `Dispose()` for you.

If you neglect to Dispose of your unmanaged resources correctly, the GC will eventually handle it for you when the object containing that resource is garbage collected (this is "finalization"). But because the garbage collector doesn't know about the unmanaged resources, it can't tell how badly it needs to release them - so it's possible for your program to perform poorly or run out of resources entirely (**memory leak**).

If you implement a class yourself that handles unmanaged resources, it is up to you to implement `Dispose()` and `Finalize()` correctly.

**Dispose**:

- The `Dispose()` method is exposed to classes that implement the `IDisposable` interface. For many classes, `Dispose()` just calls the built-in `Close()` method. (An exception are database connections, where these two methods work slightly differently).

**Finalize**:

- `Finalize()`, also called the **destructor**, cannot be called explicitly in the code. **Only the GC can call it** when object becomes inaccessible.
- It **cannot be implemented directly**, only via declaring a destructor. `~MyClass() { this.Dispose(); }`
- When to implement? There may be any **unmanaged resource** for example file stream **declared at class level**. We may not know what stage or which step is appropriate to close the file. This object is being used at many places in the application. So in this scenario Finalize can be appropriate location where unmanaged resource can be released.
- It's a bit expensive to use.

Some types encapsulate disposable resources in a manner where it is easy to use and dispose of them in a single action. The general usage is often like this: open, read or write, close (Dispose). It fits very well with the `using` construct.

Others are a bit more difficult. `WaitEventHandle`s for instances are not used like this as they are used to signal from one **thread** to another. The question then becomes who should call `Dispose()` on these? As a safeguard types like these implement a `Finalize()` method, which makes sure resources are disposed when the instance is no longer referenced by the application.

Bottom line: always use `Dispose()` to dispose of unmanaged resources as soon as possible. Implement `Finalize()` only if it's really necessary.

> Finalizers (which are also called destructors) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.

> **Finalizing is ONLY for getting rid of _unmanaged_ resources**.

#### How do you inherit a class from another class in C#?

WIP

In C#, both inheritance and interface implementation are defined by the `:` operator, equivalent to _extends_ and _implements_ in Java.
The base class should always be leftmost in the class declaration.

Like Java, C# does not support multiple inheritance, meaning that classes cannot inherit from more than one class. You can, however, use interfaces for that purpose in the same way as in Java.

You can access base class members in a subclass even when those base members are overridden in the superclass using the `base` keyword. For instance, you can create a derived class which contains a method with the same signature as in the base class.

If you prefaced that method with the `new` keyword, you indicate that this is an all-new method belonging to the derived class. You could still provide a method for accessing the original method in the base class with the `base` keyword.

#### What is difference between “is” and “as” operators in C#?

`is`:

- The `is` operator is a **type-testing _keyword_** that checks if the result of an expression is compatible with a given type, or tests an expression against a pattern.
- Simple type testing: `dog is Animal`
- Pattern matching (Type pattern):
  - When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.
  - It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion. The general form of the is type pattern is: `expr is type varname`
  - `if (o is Employee e) return e.ToString();`

`as`:

- Used to **explicitly convert an expression** to a given type if its runtime type is compatible with that type.
- The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.
- If the conversion is not possible, the as operator returns `null`.
- Unlike a cast expression, the `as` operator **never throws an exception**.

#### What are indexers in C# .NET?

WIP

Indexers allow instances of a class or struct to be **indexed just like arrays** (or dictionaries, for that matter). The indexed value can be set or retrieved without explicitly specifying a type or instance member (generic). Indexers **resemble _properties_** except that their accessors take parameters.

Overview:

- Indexers enable objects to be indexed in a similar manner to arrays.
- A `get` accessor returns a value. A `set` accessor assigns a value.
- The `this` keyword is used to define the indexer.
- The `value` keyword is used to define the value being assigned by the `set` accessor.
- Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.
- Indexers can be overloaded.
- Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.

```csharp
public List<T> Container { get; set; }

public T this[int i]
        {
            get { return Container[i]; }
            set { Container[i] = value; }
        }
```

#### What is the difference between returning IQueryable<T> vs. IEnumerable<T>?

WIP

The difference is that `IQueryable<T>` is the interface that allows **LINQ**-to-SQL (LINQ-to-anything really) to work. So if you further refine your query on an `IQueryable<T>`, that query will be executed in the database, if possible.

For the `IEnumerable<T>` case, it will be LINQ-to-object, meaning that all objects matching the original query will have to be loaded into memory from the database.

This is quite an important difference, and working on `IQueryable<T>` can in many cases save you from returning too many rows from the database. Another prime example is doing paging: If you use `Take` and `Skip` on `IQueryable<T>`, you will only get the number of rows requested; doing that on an `IEnumerable<T>` will cause all of your rows to be loaded in memory.

> The main difference arises when you work with a DB (or any remote data source). So the difference between IQueryable and IEnumerable is about _where_ the **filter logic** is executed. In case of Enumerable it executed in the C# part, in case of IQueryable **only the requested records** return back.

#### What is LINQ? Explain the idea of extension methods.

WIP

**Language-Integrated Query (LINQ)** is the name for a set of technologies based on the integration of query capabilities directly into the C# language.

Traditionally, queries against data are expressed as simple strings without **type checking** at compile time or **IntelliSense support**. Furthermore, you have to learn a **different query language** for each type of data source: SQL databases, XML documents, various Web services, and so on.

**With LINQ, a query is a first-class language construct**, just like classes, methods, events. You write queries against strongly typed collections of objects by using language keywords and familiar operators. The LINQ family of technologies provides a **consistent query experience** for:

- objects **(LINQ to Objects)**,
- relational databases **(LINQ to SQL)**,
- and XML **(LINQ to XML)**.

The standard query operators are the methods that form the LINQ pattern. Most of these methods operate on **sequences**, where a sequence is an object whose type implements the `IEnumerable<T>` interface or the `IQueryable<T>` interface. The standard query operators provide query capabilities including **filtering**, **projection**, **aggregation**, **sorting** and more.

Although it looks as if `IEnumerable<T>` has been redefined to include these additional methods, in fact this is not the case. The standard query operators are implemented as a new kind of method called **extension methods**.

Extension methods "extend" an existing class (type); they can be **called as if they were instance methods** on the class (type). The standard query operators extend `IEnumerable<T>` and that is why you can write `numbers.Where(...)`.

> To get started using LINQ, all that you really have to know about extension methods is how to bring them into scope in your application by using the correct using directives. From your application's point of view, an extension method and a regular instance method are the same.

> For readability, use Query syntax over Method syntax whenever possible.

#### What are the advantages and disadvantages of lazy loading?

WIP

**Lazy loading** (also called* on-demand loading*) is an **optimization technique** for the online content, be it a website or a web app.

Instead of loading the entire web page and rendering it to the user in one go as in _bulk loading_, the concept of lazy loading assists in **loading only the required section** and delays the remaining, until it is needed by the user.

Advantages:

- On-demand loading **reduces time consumption** and **memory usage** thereby **optimizing content delivery**. Only a fraction of the web page is loaded at first, which takes considerably less time, while the loading of the rest of the section is delayed which saves storage. All of this enhances UX as the requested content is fed in no time.
- Unnecessary code execution is avoided.
- Optimal usage of time and space resources makes it a cost-effective approach from the point of view of business persons (website owners).

Disadvantages:

- The extra lines of code, to be added to the existing ones, to implement lazy load **makes the code a bit complicated**.
- May affect **SEO** (the website's ranking on search engines) sometimes, due to improper indexing of the unloaded content.

#### How to use of “yield” keyword? Mention at least one practical scenario where it can be used?

WIP

When you use the `yield` contextual keyword in a statement, you indicate that the method, operator, or get accessor in which it appears is an **iterator**.

An iterator is used to perform a custom iteration over a collection. An iterator can be a _method_ or a _get accessor_. An iterator uses a `yield return` statement to **return each element** of the collection **one at a time**.

You call an iterator by using a `foreach` statement. Each iteration of the foreach loop calls the iterator. When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained. Execution is restarted from that location the next time that the iterator is called.

#### What are attributes in C#? Give some examples of usage of them.

WIP

Attributes provide a powerful method of associating **_metadata_**, or _declarative information_, with code (assemblies, types, methods, properties, and so forth). After an attribute is associated with a program entity, the **attribute can be queried at run time** by using a technique called **reflection**.

Attributes have the following properties:

- Attributes add **metadata** to your program. Metadata is information about the types defined in a program. All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.
- You can **apply one or more attributes** to entire **assemblies**, **modules**, or smaller program elements such as **classes** and properties.
- Attributes **can accept arguments** in the same way as methods and properties.
- Your program can examine its own metadata or the metadata in other programs by using **reflection**.

Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid. In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.

Common uses for Attributes:

- (Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the _SOAP protocol_).
- (Describing how to _marshal_ method parameters when interoperating with native code).
- (Describing the _COM properties_ for classes, methods, and interfaces).
- (Calling _unmanaged code_ using the `DllImportAttribute` class).
- (Describing your _assembly_ in terms of title, version, description, or trademark).
- Describing which members of a class to **serialize** for persistence.
- Describing how to **map** between **class members** and **XML nodes** for **_XML serialization_**.
- (Describing the security requirements for methods).
- (Specifying characteristics used to enforce security).
- (Controlling optimizations by the _just-in-time (JIT) compiler_ so the code remains easy to debug).
- Obtaining information about the caller to a method.
- Control how **tests** are executed (NUnit for example).

**Reflection**:

Reflection is the ability of a managed code to read its own metadata for the purpose of finding assemblies, modules and type information during runtime.

In other words, reflection provides objects that encapsulate assemblies, modules and types. A program reflects on itself by extracting metadata from its assembly and using that metadata either to inform the user or to modify its own behavior.

The `System.Reflection` namespace contains classes and interfaces that provide a managed view of loaded types, methods, and fields, with the ability to dynamically create and invoke types.

> Reflection provides objects (of type `Type`) that describe assemblies, modules, and types. You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties. If you are using attributes in your code, reflection enables you to access them.

```csharp
// Using GetType to obtain type information
Type type = 123.GetType();

Console.WriteLine(type); // The output is: System.Int32
```

> When writing a C# code that uses reflection, the coder can use the `typeof` operator to get the object's type or use the `GetType()` method to get the type of the current instance.

**Marshaling**:

Marshaling is the process of transforming types when they need to cross between managed and native code.

Marshaling is needed because the types in the managed and unmanaged code are different. In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc.

#### By what mechanism does NUnit know what methods to test?

WIP

NUnit uses **attributes** to control how tests are executed.

#### What is the GAC? What problem does it solve?

WIP

Each computer where the CLR is installed has a machine-wide code cache called the **global assembly cache**. The GAC stores assemblies that are to be shared by several applications on the computer. This area is typically the folder under windows or winnt in the machine.

Advantages:

- Only one place to update your assemblys.
- You use a little less hard drive space.

Disadvantages:

- If you need to update only one website, you can't. You may end with the other websites in the webserver broken.

GAC is more suitable for frameworks where there is expectation for library to be shared among more applications. In 99% of cases, you don't need it.

> Virtual environments?

#### What is the largest number you can work with in C#?

WIP

The `BigInteger` type is an immutable type that represents an **arbitrarily large integer** whose value in theory has no upper or lower bounds. (You can go as far as your RAM lets you).

### Database

#### How can you connect your application to a database server? What are the possible ways?

Using a low-level technology like _JDBC_ (Java Database Connectivity) API is one way.
Use `PGSimpleDataSource` to establish connection:

1. Create DataSource:
   First, we must create a class that will establish a _connection_ with a database. Let's name it 'BookDatabaseManager'.
   Our DBM will have a method `connect()` that will create a `DataSource` using `PGSimpleDataSource`.
   This is the base code:

```java
private DataSource connect() throws SQLException {
  PGSimpleDataSource dataSource = new PGSimpleDataSource();
  return dataSource;
}
```

2. Connect to a specific database:
   To get this code actually running, we must define what database, user and password `PGSimpleDataSource` should use.

```java
private DataSource connect() throws SQLException {
  PGSimpleDataSource dataSource = new PGSimpleDataSource();
  dataSource.setDatabaseName("books");
  dataSource.setUser("admin");
  dataSource.setPassword("admin");
  return dataSource;
}
```

3. Test the connection:
   One last thing we will do in this method is to test whether connection can be established.

```java
// connecting to database ...

System.out.println("Trying to connect...");
dataSource.getConnection().close();
System.out.println("Connection OK");

return dataSource;
```

Line `dataSource.getConnection().close();` opens and closes the connection. If this operation did not throw any exceptions, you are good to go!

#### What do you know about database normalization?

Database normalization is the restructuring process by which the database is organized into tables and columns, in order to reduce data redundancy and improve data integrity. The idea is that tables should be about a specific topic and only columns that are related to that topic are included in the table.
A fully normalized database allows its structure to be extended to accommodate new types of data without changing existing structure too much. As a result, applications interacting with the database are minimally affected. Normalized relations, and the relationship between one normalized relation and another, mirror real-world concepts and their interrelationships.

Database normalization is useful because it minimizes duplicate data in any single table, and allows for data in the database to grow independently of each other (ie. Types of car engines can grow independent of each type of car). As a trade-off, queries get slightly more complex since they have to be able to find data from different parts of the database, and performance issues can arise when working with many large tables.

In order to answer questions about an entity that has data spanning multiple tables in a normalized database, we need to learn how to write a query that can combine all that data and pull out exactly the information we need.
