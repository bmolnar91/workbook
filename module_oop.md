# OOP questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?
The 'fail-fast' principle encourages us to fail fast and early: If an error occurs, fail immediately and visibily. If something unusually or unexpectedly occurs, let the software fail immediately instead of postponing the failure or working around the failure. The longer it takes for a bug to appear on the surface, the longer it takes to fix and the greater it costs.

Fail-fast makes bugs and failures appear sooner, thus:
* Bugs are
    - earlier to detect,
    - easier to reproduce and
    - faster to fix.  
* It’s faster to stabilize softwares.
* Fewer bugs and defects will go into production, thus leading to higher-quality and more production-ready software.
* The cost of failures and bugs are reduced.


## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?
IN PROGRESS

Iterate through the list using 2 pointers. When the "fast" pointer reaches the end, the "slow" pointer will point to the middle element.


#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?
IN PROGRESS

Loop over the array, and insert every element into a HashSet while checking the return value. If add() returns false, it means that element is not allowed in the Set, and that is your duplicate.
Complexity: O(n)


#### What is a linked list? How to find if a linked list has a loop?
IN PROGRESS

'LinkedList' is a data structure consisting of a group of nodes which together represent a sequence. Each node is composed of data and a link to the next node in the sequence.

The most notable difference between the LinkedList and the ArrayList is in the way they store objects.
The ArrayList is better for storing and accessing data, as it is very similar to a normal array.
The LinkedList is better for manipulating data, such as making numerous inserts and deletes.

In addition to storing the object, the LinkedList stores the memory address (or link) of the element that follows it. It's called a LinkedList because each element contains a link to the neighboring element.

//
- Use an ArrayList when you need rapid access to your data OR if you want to add/remove items at the END of your list. "Use an ArrayList normally".
- Use a LinkedList when you need to make a large number of inserts and/or deletes.
//


#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?
IN PROGRESS

ArrayList:
- add(): O(1)
- add(intex, element): O(n)
- get(): O(1)
- indexOf(): O(n)
- contains(): O(n)

LinkedList:
- add(): O(1) at any position
- get(): O(n)
- remove(): O(1)
- contains(): O(n)

HashMap:
- containsKey(): O(1)
- get(): O(1)
- put(): O(1)
- remove(): O(1)

Bubble Sort: O(n^2)

Quicksort:
- Average: O(log n)
- Worst case: O(n^2)

Binary Search Tree:
- Average: O(log n)
- Worst case: O(n)


#### How does HashMap work?
IN PROGRESS

Arrays and Lists store elements as ordered collections, with each element given an integer index.

'HashMap' is used for storing data collections as key and value pairs. One object is used as a key (index) to another object (the value).
The 'put', 'remove', and 'get' methods are used to add, delete, and access values in the HashMap.

A HashMap cannot contain duplicate keys. Adding a new item with a key that already exists overwrites the old element.
The HashMap class provides 'containsKey' and 'containsValue' methods that determine the presence of a specified key or value.
If you try to get a value that is not present in your map, it returns the value of null.

//'null' is a special type that represents the absence of a value.//


#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)
IN PROGRESS

If immutable, the object's hashcode won't change and it allows caching the hashcode of different keys which makes the overall retrieval process very fast.
Also for mutable objects, the hashCode() might be dependent on fields that could change, if this happens you won't be able to find the key (and its value) in the HashMap since hashCode() returns different value.


### Other

#### What is a garbage collector, in a nutshell?

## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?
IN PROGRESS

Assigning a value of one type to a variable of another type is known as 'Type Casting'.
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
IN PROGRESS

All catch blocks should be ordered from most specific to most general.
Following the specific exceptions, you can use the 'Exception' type to handle all other exceptions as the last catch.


### Object-oriented

#### What is a class?
IN PROGRESS

A class is a user defined blueprint or prototype from which objects are created.  It represents the set of properties or methods that are common to all objects of one type.


#### What is an object?
IN PROGRESS

It is a basic unit of Object Oriented Programming and represents the real life entities. A typical Java program creates many objects which interact by invoking methods.

An object consists of:
- State: It is represented by 'attributes' of an object. It also reflects the properties of an object.
- Behavior: It is represented by 'methods' of an object. It also reflects the response of an object with other objects.
- Identity: It gives a unique 'name' to an object and enables one object to interact with other objects.


#### What is a constructor?
IN PROGRESS

Constructors are special methods invoked when an object is created and are used to initialize them.
A constructor can be used to provide initial values for object attributes.
- A constructor name must be same as its class name.
- A constructor must have no explicit return type.

The constructor is called when you create an object using the new keyword.

//You can think of constructors as methods that will set up your class by default, so you don’t need to repeat the same code every time.//

//Java automatically provides a default constructor, so all classes have a constructor, whether one is specifically defined or not.//


#### Do we require parameter for constructors?
IN PROGRESS

Parameters are not required for constructors.
A single class can have multiple constructors with different numbers of parameters.


#### What is an interface?
An interface is a completely 'abstract' class that contains only 'abstract' methods.
Some specifications for interfaces:
* Defined using the 'interface' keyword.
* May contain only public static final variables.
* Cannot contain a constructor because interfaces cannot be instantiated.
* Interfaces can extend other interfaces.
* A class can implement any number of interfaces.

Interfaces have the following properties:
* An interface is implicitly abstract. You do not need to use the 'abstract' keyword while declaring an         interface.
* Each method in an interface is also implicitly abstract, so the abstract keyword is not needed.
* Methods in an interface are implicitly public.

Use the 'implements' keyword to use an interface with your class.
When you implement an interface, you need to override all of its methods.

//A class can inherit from just one superclass, but can implement multiple interfaces.//

Java 8 has added the concept of interface 'default methods' to Java interfaces. An interface default method can contain a default implementation of that method.
Classes that implement the interface but which contain no implementation for the default interface will then automatically get the default method implementation (and the code doesn't break).

You mark a method in an interface as a default method using the 'default' keyword.

//Default methods can be overriden.//

//In some cases it can make sense to define constants in an interface, otherwise it's better to avoid variables/fields altogether.//

//Static methods in interfaces can be useful when you have some utility methods you would like to make available, which fit naturally into an interface related to the same responsibility. For instance, a Vehicle interface could have a printVehicle(Vehicle v) static method.//


#### What are access modifiers?
IN PROGRESS

The access modifiers in Java specify the accessibility or scope of a field, method, constructor, or class. We can change the access level of fields, constructors, methods, and classes by applying the access modifier on it.


#### What is data hiding?
IN PROGRESS

The idea behind 'encapsulation' is to ensure that implementation details are not visible to users. The variables of one class will be hidden from the other classes, accessible only through the methods of the current class. This is called 'data hiding'.

To achieve encapsulation in Java, declare the class' variables as private and provide public setter and getter methods to modify and view the variables' values.


#### Can a static method use non-static members?
No. One of the basic rules of working with static methods is that you can’t access a nonstatic method or field from a static method because the static method doesn’t have an instance of the class to use to reference instance methods or fields.


#### What is the difference between hiding a static method and overriding an instance method?
IN PROGRESS

Overriding an instance method is based on late binding, whereas hiding a static method is based on early binding.

When you override a method, you still get the benefits of run-time polymorphism, and when you hide, you don't.


#### Define the following terms: Instantiation, Attribute, Method
Instantiation:
  Creating a new instance of a class is called 'instantiation'. The 'new' keyword is used to instantiate a class object.

Attribute:
  An attribute is another term for a field. It's typically a public constant or a public variable that can be accessed directly.

Method:
  A method is a block of code which only runs when it is called. Methods (also known as functions) are used to perform certain actions.


#### Could we access a static variable (or method) from a non-static method? Why?
Yes, instance methods can access class variables and class methods directly.


#### Could we access a non-static variable (or method) from a static method? Why?
No, class methods cannot access instance variables or instance methods directly — they must use an object reference. Also, class methods cannot use the *this* keyword as there is no instance for *this* to refer to.


#### How many instances you have of a static variable of a given class?
Only one.


#### Why is it not a good practice to write a lot of static methods?
Our code may become too specific/rigid, which makes it hard to extend/maintain it.


//The question you have to ask before typing static is the following: "If there were more instances of this class, would they share this state/behaviour?" Don't use static unless the answer is 'yes'.//

//We cannot and should not think ahead of all the possible upgrades and specification changes. We have to find some golden mean when designing our classes between the too specific/rigid and the overgeneralized extremes. Try to write as flexible code as you can without putting in significant extra work for that! Use YAGNI!//


#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?
Class members represent states and behaviours connected to the 'class' itself, all of its instances at the same time.

Benefits:
* There's one version of them in memory, bound at compile-time (early binding).
* Depending on access level, class members can be reached from anywhere without needing an instance of the class.

When to use: see above


#### What is the ‘this’ reference?
IN PROGRESS

Within an instance method or a constructor, `this` is a reference to the current object — the object whose method or constructor is being called. You can refer to any member of the current object from within an instance method or a constructor by using `this`.

The most common reason for using the `this` keyword is because a field is shadowed by a method or constructor parameter.


#### What are base class, subclass and superclass?
Tied with the concept of inheritance.
The class inheriting the properties of another is the 'subclass' (also called 'derived class', or 'child class'); the class whose properties are inherited is the 'superclass' ('base class', or 'parent class').

To inherit from a class, use the `extends` keyword.

The purpose of inheritance is twofold:
* to design a class structure in line with the real structure of the problem domain;
* to prevent code duplication: common parts of different classes (both variables and methods) should be written once and used through a common class.


#### Draw an object oriented family (as entities, with relations) on the whiteboard.
#### Difference between overloading and overriding?
Static Binding or Early Binding:
  The binding which can be resolved at compile time by compiler is known as static or early binding. The binding of 'static', 'private' and 'final' methods is compile-time. The reason is that the these method cannot be overridden and the type of the class is determined at the compile time.

Dynamic Binding or Late Binding:
  When compiler is not able to resolve the call/binding at compile time, such binding is known as Dynamic or Late Binding. Method 'Overriding' is a perfect example of dynamic binding as in overriding both parent and child classes have same method and in this case the type of the object determines which method is to be executed.

Differences:
* Static binding happens at compile-time while dynamic binding happens at runtime.
* Binding of private, static and final methods always happen at compile time since these methods cannot be overridden.
When the method overriding is actually happening and the reference of parent type is assigned to the object of child class type then such binding is resolved during runtime.
* The binding of overloaded methods is static and the binding of overridden methods is dynamic.


#### What are the Object Oriented Principles? Explain the concepts with realistic examples!
IN PROGRESS

- Encapsulation:
    The packing of data and methods into a single component.
    - Control of the way data is accessed or modified
    - More flexible and easily changed code
    - Ability to change one part of the code without affecting other parts
    //When a variable is hidden by private modifier and can be accessed only through getter and setter, it is encapsulated.//

- Inheritance:
    Inheritance is the process that enables one class to acquire the properties (methods and variables) of another. With inheritance, the information is placed in a more manageable, hierarchical order.

- Polymorphism:
    Polymorphism, which refers to the idea of "having many forms", occurs when there is a hierarchy of classes related to each other through inheritance.
    A call to a member method will cause a different implementation to be executed, depending on the type of the object invoking the method.

- Abstraction:
    Data abstraction provides the outside world with only essential information, in a process of representing essential features without including implementation details.
    A good real-world example is a book. When you hear the term book, you don't know the exact specifics, such as the page count, the color, or the size, but you understand the idea, or abstraction, of a book.
    The concept of abstraction is that we focus on essential qualities, rather than the specific characteristics of one particular example.

    In Java, abstraction is achieved using 'abstract' classes and interfaces.
    An abstract class is defined using the abstract keyword.
    - If a class is declared abstract it cannot be instantiated (you cannot create objects of that type).
    - To use an abstract class, you have to inherit it from another class.
    - Any class that contains an abstract method should be defined as abstract.

    An abstract method is a method that is declared without an implementation (without braces, and followed by a semicolon):
        abstract void walk();

    // Every Animal makes a sound, but each has a different way to do it. That's why we define an abstract class Animal, and leave the implementation of how they make sounds to the subclasses.
    This is used when there is no meaningful definition for the method in the superclass. //

    //An abstract class is a class that cannot be instantiated, meaning that you cannot create new instances of an abstract class. The sole purpose of an abstract class is to function as a base for other subclasses.//


#### What is method overloading?
IN PROGRESS

Happens at compile time. A subclass can define a behavior that's specific to the subclass type, meaning that a subclass can implement a parent class method based on its requirement.
When methods have the same name, but different parameters, this feature is known as method 'overloading', also known as 'compile-time polymorphism'.

In order to overload a method, the argument lists of the methods must differ in either of these:
* number of parameters
* data type of parameters
* sequence of Data type of parameters

If two methods have same name, same parameters and have different 'return type', then this is NOT a valid method overloading example - this will throw compilation error.

//Very useful for when you need the same method functionality for different types of parameters.//


#### What is method overriding?
Happens at runtime. A subclass can define a behavior that's specific to the subclass type, meaning that a subclass can implement a parent class method based on its requirement.
This feature is known as method 'overriding', also known as 'runtime polymorphism', or 'dynamic method dispatch'.

Rules for Method Overriding:
    - Should have the same return type and arguments
    - The access level cannot be more restrictive than the overridden method's access level (Example: If      the superclass method is declared public, the overriding method in the sub class can be neither         private nor protected)
    - A method declared final or static cannot be overridden
    - If a method cannot be inherited, it cannot be overridden
    - Constructors cannot be overridden

The '@Override' annotation is used to make your code easier to understand, because it makes it more obvious when methods are overridden.
It also instructs the compiler: if you make any mistake such as wrong method name, wrong parameter types while overriding, you would get a compile time error.

Rules of method overriding in Java:
* Argument list: The argument list of overriding method (method of child class) must match the Overridden method(the method of parent class). The data types of the arguments and their sequence should exactly match.
* Access Modifier of the 'overriding' method (method of subclass) cannot be more restrictive than the 'overridden' method of parent class. 
* Private, static and final methods cannot be overridden as they are local to the class. However static methods can be re-declared in the sub class, in this case the sub-class method would act differently and will have nothing to do with the same static method of parent class.
* Overriding method (method of subclass class) can throw unchecked exceptions, regardless of whether the overridden method (method of superclass) throws any exceptions or not. However the overriding method should not throw checked exceptions that are new or broader than the ones declared by the overridden method.
* Binding of overridden methods happen at runtime which is known as dynamic binding.
* If a class is extending an abstract class or implementing an interface then it has to override all the abstract methods unless the class itself is a abstract class.


#### Explain how object oriented languages attempt to simplify memory management for Programmers.
#### Explain the “Single Responsibility” principle!
#### What is an object oriented program? Explain, show.
#### How do you make a class immutable? What do you need to watch out for?
#### How many instances can be created for an abstract class?
None.

Abstract classes cannot be instantiated. The purpose of an abstract class is to function as a base for subclasses.


## Programming languages

### Java

#### What is autoboxing and unboxing?
#### If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?
IN PROGRESS

The 'short' type. 0-200 is well within the bounds of the 16 bits it uses.


#### What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?
General convention for a variable’s scope is, it is accessible only within the block in which it is declared.

1. Class variables:
  A variable which is declared inside a class, outside all the blocks and is marked static is known as a class variable.The lifetime of a class variable is until the end of the program or as long as the class is loaded in memory.

2. Instance variables:
  A variable which is declared inside a class and outside all the methods and blocks is an instance variable. Lifetime of an instance variable is until the object stays in memory.

3. Local variables:
  All other variables which are not instance and class variables are treated as local variables including the parameters in a method.The lifetime of a local variable is until the control leaves the block in which it is declared.


#### What is the purpose of the ‘equals()’ method?
Each object has a predefined `equals()` method that is used for semantical equality testing.

To make it work for our classes, we need to override it and check the conditions we need.
There is a simple and fast way of generating the equals() method, other than writing it manually (from within the IDE).


#### What is the difference between '==' and 'equals()'?
When you compare objects using the equality testing operator (`==`), it actually compares the references and not the object values.

The `equals()` method is used for semantical equality testing.


#### What does the ‘static’ keyword mean?
IN PROGRESS

When you declare a variable or a method as 'static', it belongs to the 'class', rather than to a specific 'instance'. This means that only one 'instance' of a static member exists, even if you create multiple objects of the class, or if you don't create any. It will be 'shared' by all objects.

//It’s a common practice to use upper case when naming a static variable, although not mandatory.//

!
//Static fields are created and initialized when the class is first loaded. That happens when a static member of the class is referred to or when an instance of the class is created, whichever comes first.//
!

#### Why is the main() method declared as static? Explain.
IN PROGRESS

One of the basic rules of working with static methods is that you can’t access a nonstatic method or field from a static method because the static method doesn’t have an 'instance' of the class to use to reference instance methods or fields.

The best-known static method is 'main', which is called by the 'Java runtime' to start an application. The main method must be static, which means that applications run in a static context by default.


#### What is the default access modifier in a class?
default (optional): The class is accessible only by classes in the same package. Also called package-private.


#### What is the JVM?
IN PROGRESS

Stands for 'Java Virtual Machine'.

The JVM has two primary functions: to allow Java programs to run on any device or operating system (known as the "Write once, run anywhere" principle), and to manage and optimize program memory.

//The JVM manages system memory and provides a portable execution environment for Java-based applications.//


#### What is the difference between the JRE and the JDK?
JRE:
    - Stands for 'Java Runtime Environment'.
    - The JRE provides the minimum requirements for executing a Java application; it consists of the Java Virtual Machine (JVM), core classes, and supporting files.

JDK:
    - Stands for 'Java Development Kit'.
    - The JDK is a software development environment used for developing Java applications and applets. It     includes the
        Java Runtime Environment (JRE),
        an interpreter/loader (Java),
        a compiler (javac),
        an archiver (jar),
        a documentation generator (Javadoc),
        and other tools needed in Java development.

//
JRE = JVM + Library Classes
JDK = JRE + Development Tools
//


#### What is the difference between long and Long?
IN PROGRESS

long: (primitive)
- The long data type is a 64-bit signed Java primitive data type.
- It is used when the result of calculations on whole numbers may exceed the range of the int data type.
- Its range is -2^63 to 2^63 - 1.
- All whole numbers in the range of long are called integer literals of long type.
- An integer literal of type long always ends with ‘L’ (or lowercase ‘l’).

Long: (class)
- The Long Wrapper Class defines two constants to represent maximum and minimum values of long data type, Long.MAX_VALUE and Long.MIN_VALUE.


#### Can a long store bigger numbers than a Long?
IN PROGRESS

No. 


#### What kind of packages do you know under java.util.* ? Bring at least 3 examples.
IN PROGRESS

Packages are used to avoid name conflicts and to control access to classes.
A 'package' can be defined as a group made up of similar types of classes, along with sub-packages.

Two major results occur when a class is placed in a package.
    - First, the name of the package becomes a part of the name of the class.
    - Second, the name of the package must match the directory structure where the corresponding class file   resides.

Arrays, Scanner ...


#### What are the access modifiers in Java? Which one could we use for class?
IN PROGRESS

Top level (classes):
* default (no modifier): The class is accessible only by classes in the same package. Also known as           'package-private'.
* public: The class is accessible by any other class.

Member level (attributes and methods):
* private: Accessible only within the declared class itself.
* default (no modifier): A variable or method declared with 'no access control modifier' is available to      any other class in the same package. Also known as 'package-private'.
* protected: Provides the same access as the 'default' access modifier, with the addition that subclasses     can access 'protected' methods and variables of the superclass.
  //Makes the members visible (or "public") only to the subclasses//
* public: Accessible from any other class.

//It's a best practice to keep the variables within a class private. The variables are accessible and modified using Getters and Setters.//


#### Can an “enum” contain methods in Java? Explain.
IN PROGRESS

No.

An Enum is a special type used to define collections of constants.
Basically, Enums define variables that represent members of a fixed set.

You should always use Enums when a variable (especially a method parameter) can only take one out of a small set of possible values.
If you use Enums instead of integers (or String codes), you increase compile-time checking and avoid errors from passing in invalid constants, and you document which values are legal to use.

//Some sample Enum uses include month names, days of the week, deck of cards, etc.//


#### When would you use a private/protected/public attribute? What is the difference?
#### How do you prevent developers from subclassing a class?
#### How do you prevent developers from overriding a method in a subclass?
#### How do you prevent developers from changing the value of a variable?
#### Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!
IN PROGRESS

Java has Currency class that represents the ISO 4217 currency codes. BigDecimal is the best type for representing currency decimal values.

//Note: Never store money in a floating point format as they have imprecisions in their representation.//


#### What happens if you try to call something, that you have no access to, because of data hiding?
#### What happens if you try to delete/drop an item from an array, while you are iterating over it?
#### What happens if you try to delete/drop/add an item from a List, while you are iterating over it?
IN PROGRESS

A 'ConcurrentModificationException' occurs. You need an Iterator to do that.


#### What happens if you try to add an item to the end of an array, while you are iterating over it?
#### If you need to access the iterator variable after a for loop, how would you do it?
IN PROGRESS

An 'Iterator' is an object that enables to cycle through a collection, obtain or remove elements.
Before you can access a collection through an iterator, you must obtain one. Each of the collection classes provides an iterator() method that returns an iterator to the start of the collection. By using this iterator object, you can access each element in the collection, one element at a time.


#### Which interfaces extend the Collection interface in Java. Which classes?
#### What is the connection between equals() and hashCode()? How are they used in HashMap?
#### What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?
IN PROGRESS

An 'exception' is an object that’s created when an error occurs in a Java program, and Java can’t automatically fix the error. The exception object contains information about the type of error that occurred.

The most important information — the cause of the error — is indicated by the name of the exception class used to create the exception. You usually don’t have to do anything with an exception object other than figure out which one you have.

A 'checked exception' is an exception that the compiler requires you to provide for it one way or another. If you don’t, your program doesn’t compile. //Checked when compiled//

An 'unchecked exception' is an exception that you can provide for, but you don’t have to. //Checked at runtime//

//ALL exceptions other than Runtime Exceptions are known as Checked exceptions.//

//Object <- Throwable <- Exception <- RuntimeException*; IOException, etc.//


#### What is Error in Java and how does it relate to Exception?
IN PROGRESS

Errors indicate that something severe enough has gone wrong, the application should crash rather than try to handle the error.

Exceptions are events that occurs in the code. A programmer can handle such conditions and take necessary corrective actions.


#### When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?
The circumstances that prevent execution of the code in a finally block are:
* The death of a Thread.
* Using of the System.exit() method.
* Due to an exception arising in the finally block.
It always runs otherwise (even despite a return statement).

It's a good practice to use 'close()' inside finally block. You can be sure that all input and output streams are closed properly regardless of whether the exception occurs or not.
It is the right place to close files, recover resources, and otherwise clean up after the code enclosed in the try block.


#### What is the largest number you can work with in Java?
java.math.BigInteger

(Integer.MAX_VALUE is approx. 2^31, which exceeds the 32bit memory.)

BigInteger can grow as large as your ram.


#### When you use method overriding, can you change the access level of the method, from protected to public? Why? When you use method overriding, can you change the access level of the method, from public to protected? Why?
You can expand, but not narrow, the accessibility of an ovverriden method.

//SUPERCLASS access modifier <= SUBCLASS access modifier//


#### Can the main method be overridden? Explain your answer!
No. Because it's a static method, it can't be overriden (but it can be overloaded!).

//The best-known static method is main, which is called by the Java runtime to start an application. The main method must be static, which means that applications run in a static context by default.//


#### When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?
If the superclass method declares an exception, subclass overridden method can declare same, subclass exception or no exception but cannot declare parent exception.


#### When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?
Unchecked exceptions: Yes.

Checked exceptions: The overriding method must NOT throw checked exceptions that are new or broader than those declared by the overridden method. For example, a method that declares a FileNotFoundException cannot be overridden by a method that declares a SQLException, Exception, or any other non-runtime exception unless it's a subclass of FileNotFoundException.


#### What does "final" mean in case of a variable, method or a class?
IN PROGRESS

Use the 'final' keyword to mark a variable constant, so that it can be assigned only once.
    public static final double PI = 3.14;

Methods and classes can also be marked final.
    - methods: can't be overridden
    - classes: can't be subclassed


#### What is the super keyword?
IN PROGRESS

You can access the superclass from the subclass using the 'super' keyword.
For example, super.var accesses the var member of the superclass.

The super keyword is similar to this keyword. It is mainly used to:
* differentiate the members of superclass from the members of subclass, if they have same names
* invoke the superclass constructor from subclass


#### What are “generics”? When to use? Show examples.
In a nutshell, generics enable *types* (classes and interfaces) to be parameters when defining classes, interfaces and methods.

Abstract types declared between angle brackets<> (a.k.a. *diamond operator*) can be used as wildcards.

Code that uses generics has many benefits over non-generic code:
* Stronger type checks at compile time.
  A Java compiler applies strong type checking to generic code and issues errors if the code violates type safety. Fixing compile-time errors is easier than fixing runtime errors, which can be difficult to find.
* Elimination of casts.
* Enabling programmers to implement generic algorithms.
  By using generics, programmers can implement generic algorithms that work on collections of different types, can be customized, and are type safe and easier to read.


#### What is the benefit of having “generic” containers?
See above.


#### Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?
In a nutshell: There are multiple choices, the optimal solution depends on what kind of data is to be transferred. If data is String: most simple: System.out/System.in + ProcessBuilder; For low number of processes(<10): Through Sockets; For large number of processes: JMS; If data can be even Objects as well: Less processes: RMI; More processes: JMS; +Http


#### What is an annotation? What can be annotated and how? Show examples.
Annotations, a form of metadata, provide data about a program that is not part of the program itself. Annotations have no direct effect on the operation of the code they annotate.

Annotations have a number of uses, among them:
* Instructions to the compiler:
  There are three built-in annotations available in Java (`@Deprecated`, `@Override` & `@SuppressWarnings`) that can be used for giving certain instructions to the compiler.
* Compile-time instructors:
  Annotations can provide compile-time instructions to the compiler that can be further used by software build tools for generating code, XML files etc.
* Runtime instructions:
  We can define annotations to be available at runtime which we can access using java reflection and can be used to give instructions to the program at runtime.


### C&#35;

#### Explain the purpose of IL and how does it relate to CLR?
#### What does “managed code” mean?
#### What is an assembly?
#### What is the difference between an EXE and a DLL?
#### What is strong-typing versus weak-typing? Which is preferred? Why?
#### What is a namespace?
#### Explain sealed class in C#?
#### What is explicit vs. implicit conversion? Give examples of both of them.
#### Is a struct stored on the heap or stack?
#### Can a struct have methods?
#### Can DateTimes be null?
#### List out the differences between Array and ArrayList in C#?
#### How is the using() pattern useful? What is IDisposable? How does it support deterministic finalization?
#### How can you make sure that objects using dedicated resources (database connection, files, hardware, OS handle, etc.) are released as early as possible?
#### Why to use keyword “const” in C#? Give an example.
#### What is the difference between “const” and “readonly” variables in C#?
#### What is a property in C#?
#### List out two different types of errors in C#?
#### What is the difference between “out” and “ref” parameters in C#?
#### Can we override private virtual method in C#?
#### What's the difference between IEquatable and just overriding Object.Equals()?
#### Explain the differences between public, protected, private and internal. Explain access modifier – “protected internal” in C#!
#### What’s the difference between using `override` and `new` keywords when defining method in child class?
#### Explain StringBuilder class in C#!
#### How we can sort the array elements in descending order in C#?
#### Can you use a value type as a generic type argument in C#? For example when implementing an interface like (IEquatable).
#### What are Nullable Types in C#?
#### Conceptually, what is the difference between early-binding and late-binding?
#### What is delegate, event, callback, multicast delegate?
#### What is enum in C#?
#### What is null-conditional operator?
#### What is null-coalescing operator?
#### What is serialization?
#### What is the difference between Finalize() and Dispose() methods?
#### How do you inherit a class from another class in C#?
#### What is difference between “is” and “as” operators in C#?
#### What are indexers in C# .NET?
#### What is the difference between returning IQueryable<T> vs. IEnumerable<T>?
#### What is LINQ? Explain the idea of extension methods.
#### What are the advantages and disadvantages of lazy loading?
#### How to use of “yield” keyword? Mention at least one practical scenario where it can be used?
#### What are attributes in C#? Give some examples of usage of them.
#### By what mechanism does NUnit know what methods to test?
#### What is the GAC? What problem does it solve?
#### What is the largest number you can work with in C#?

### Database

#### How can you connect your application to a database server? What are the possible ways?
Examples to connect to db: Psycopg2 in Python and JDBC in Java.


#### What do you know about database normalization?
Database normalization is the restructuring process by which the database is organized into tables and columns, in order to reduce data redundancy and improve data integrity. The idea is that tables should be about a specific topic and only columns that are related to that topic are included in the table. A fully normalized database allows its structure to be extended to accommodate new types of data without changing existing structure too much. As a result, applications interacting with the database are minimally affected. Normalized relations, and the relationship between one normalized relation and another, mirror real-world concepts and their interrelationships.
