# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!

1. Capitalize SQL keywords.
2. Organize it not just horizontally, but also vertically:
   - break up your code logically into new lines, and
   - use indentation to improve readability
3. Use a syntax that prevents SQL injection attacks (wildcards etc).

#### What layers can you name in a simple web application?

**View layer**:

- The outermost layer that deals with the presentation of the content and interaction with the user.
- Communicates with the Business Logic layer
- Mainly involved technologies are:
  - markup (HTML etc.)
  - style (CSS)
  - client-side scripts (Javascript, Flash)

**Business Logic layer**:

- The central layer that deals with the logic of the program.
- Receives and transforms data from the other layers.
- Determinant part of the application logic:
  - performing all required calculations and validations
  - managing workflow
  - managing all data access for the View layer

**Data layer**:
Deepest level in the layered architecture, the data layer deals with data retrieval (databases, csv files).
Provides retrieved data for the Business Logic layer.

### Error handling

#### What error can occur, when an array does not have an element on the requested index?

Python:

- the script terminates
- results in `IndexError`: list index out of range

JavaScript:

- the script doesn't terminate
- results in `undefined`

#### What is the "finally" block, and how would you use it?

Code in a `finally` block gets executed regardless of the outcome of the try-except block before it.

#### Why should we catch special exception types?

- To easily identify errors and fix / communicate them.
- To prevent the program from crashing (if we expect the error).

### Security

#### What is SQL injection? How to protect an application against it?

A computer attack in which malicious code is embedded in a poorly-designed application and then passed to the backend database.

Steps to take:

- Input validation:
  - Sanitize the input
  - Escape/Quotesafe the input
- Parameterized queries
- Limit database permissions and segregate users
- Use stored procedures for database access
- Isolate the webserver
- Configure error reporting

#### What is XSS? How to protect an application against it?

Cross-Site Scripting (XSS) attacks are a type of _injection_, in which malicious scripts are injected into otherwise benign and trusted websites.

XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a **browser side script**, to a different end user.

The malicious script can then access any _cookies_, _session tokens_, or other sensitive information retained by the _browser_ and used with that site. These scripts can even rewrite the content of the HTML page.

Steps to take:

- Never insert untrusted data:
  - directly in a script
  - inside an HTML comment
  - in an attribute name
  - in a tag name
  - directly in CSS
- HTML escape before inserting untrusted data (framework methods, HTML entity encoding)
- Don't use `innerHTML` where you need user input, `textContent` is way better, this way the whole query will be a string and won't be executed as an HTML tag

#### How to properly store passwords?

We store hashed passwords in a database.

#### What is HTTPS?

**Hypertext Transfer Protocol Secure (HTTPS)** is the secure version of HTTP, which is the primary protocol used to send data between a web browser and a website.

HTTPS is **encrypted** in order to increase security of data transfer.
Any website, especially those that require login credentials, should use HTTPS. In modern web browsers such as Chrome, websites that do not use HTTPS are marked differently than those that are.

Technically speaking, HTTPS is not a separate protocol from HTTP. It is simply using **TLS/SSL encryption** over the HTTP protocol. HTTPS occurs based upon the transmission of **TLS/SSL certificates**, which verify that a particular provider is who they say they are.

Does HTTPS use Asymmetric or Symmetric encryption? In short:

The best answer is that it does both. TLS uses **asymmetric encryption to first establish identity** of one or both parties. Secondly, it uses **asymmetric encryption to exchange a key to a _symmetric_ cipher**. So asymmetric is **only used during the initial setup of communication (TLS-SSL handshake)**.

**Symmetric encryption** which is **used through the rest** is faster and more efficient with large amounts of data transfer. The keys are smaller which is generally why it's faster, but it's algorithm is also easier to process.

#### What is encryption and decryption?

Encryption is a way of **scrambling** data so that only authorized parties can understand the information. In technical terms, it is the process of **converting plaintext to ciphertext**. In simpler terms, encryption takes readable data and alters it so that it **appears random**.

Encryption requires the use of an **encryption key**: a set of mathematical values that both the sender and the recipient of an encrypted message know.

Although encrypted data appears random, encryption proceeds in a logical, predictable way, so that a party receiving the encrypted data and in possession of the key used to encrypt the data can _decrypt_ the data, turning it back into plaintext.

#### What is hashing?

Hash algorithms are **one way** functions. They turn any amount of data into a **fixed-length** "fingerprint" or "signature" that **cannot be reversed**. They also have the property that if the **input changes** by even a tiny bit, the resulting hash is _completely different_.

Hashing is a digital signature. It was originally designed to check if data was modified.

#### What is the difference between encryption and hashing? When would you use which?

Encryption is a method for encoding information to keep it secret. Hashing is a signature for a file or password.

Encryption:

- A technique used to maintain the _confidentiality_ of data by converting the data into an undecipherable format.
- At its core, encryption is all about asserting identity and protecting data integrity.
- The origin of encrypted messages can be _traced_, thus facilitating _authentication_ of the message source.
- In case the data gets leaked, it's easy to trace the source. In other words, it's easy to trace who did it and when, thus making auditing for accountability easy. It helps in resolving security breaches efficiently.
- Only intended parties with the right private key can read the data.
- Use encryption whenever you **need** to get the input data back out. If you're storing credit card numbers, you need to get them back out at some point, but don't want to store them plain text. So instead, store the encrypted version and keep the _key_ as safe as possible.
- Unlike hashing, encryption always produces a **unique file**.

Hashing:

- A string of numbers generated to confirm the _integrity_ of data through hashing algorithms.
- Unlike encryption, hashing serves as a checksum to ensure that a particular piece of data or a file hasn't been altered.
- Hashing is the most suitable way to securely store **passwords**.
- Hashing is helpful in comparing a value with a stored value, hence avoiding _duplication_. This can be done by storing the hash with a _salt_, and then with any future login attempts, hash the passwords that the users enter and compare it with the stored hash.
- Hashing is used in a variety of digital certificates, including _SSL certificates_.
- Hashing helps you find specific data in a huge **database**.
- Unlike with encryption, hashing may produce **hash collisions**.

#### What encryption methods do you know?

**Symmetric Encryption**:

- Symmetric-key encryption is an algorithm for cryptography that use the **same key** for both encryption of plain-text and decryption of cipher-text.
- A public key is used on the sender's side when the data is encrypted, which happens for example when you are sending a message to somebody else, the server then decrypts the message according to the public key and encrypts it again with the receiver's public key, so then he will be able to decrypt it with his own public key and get the information.
- The problem here is that the server / "man in the middle" (ISPs for example) will know both the sender and the receiver's public key and will be able to decrypt the private message.
- E.g. ROT13 cipher

**Asymmetric Encryption**:

- Instead of just one public key, you have a **key pair**: a _public key_ and a _private key_.
- The algorithm, that is used to generate the two keys, will make sure that the key pair is mathematically _linked_ to each other.
- The public key is public, you put it at the end of all e-mails, posts etc. The private key is absolutely secret.
- E.g. RSA algorithm

1. **Cryptography (encryption/decryption)**: Any message _encrypted_ with Bob's **public key** can only be **_decrypted_** with Bob's **private key**.
2. **Signature (authentication)**: Anyone with access to Alice's **public key** can **_verify_** that a message (signature) could only have been created by someone with access to Alice's **private key**.

> CA = Certificate Authority

> In cryptography a **key** is a piece of information **used in combination with an algorithm** (a _cipher_) to transform plaintext into ciphertext (encryption) and vice versa (decryption).

> A cipher can be **reciprocal** if it is used for both encryption and decryption, or **non-reciprocal** if a transformation to the key is required when using it in reverse.

#### What hashing methods do you know?

Salt:
Salts are a random set of characters that are appended to the user's password before(!) they are hashed. Salts are stored in plain text along with the hashed output, so the website knows what salt to use when it comes to verify the password. Brute Force attacks will still be an issue, but Rainbow tables and Dictionary attacks won't work because it's computationally infeasible to generate rainbow tables for every possible salt.

Pepper:
A very short random string of characters appended to the end of the password. Peppers are random and different in each password. The pepper is not stored.

Bcrypt:
Uses salts built into the generated hashes to prevent rainbow table and dictionary attacks.

MD5:
128 bit/32 characters long - very poor security - fastest computation

SHA:
SHA: 160 bit/40 characters long - moderate security - second fastest

#### How/where would you store sensitive data (like db password, API key, ...) of your application?

Storing secrets in the OS environment.

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?

Stack:

- A linear data structure in which elements can be inserted and deleted only from one side of the list, called the top.
- Based on the _LIFO_ principle
- Insert operation is called push operation
- Delete operation is called pop operation
- We maintain only _1 pointer_ (-> top)

Queue:

- A linear data structure in which elements can be inserted only from one side of the list called rear, and the elements can be deleted only from the other side called the front.
- Based on the _FIFO_ principle
- Insert operation is called enqueue operation
- Delete operation is called dequeue operation
- We maintain _2 pointers_ (-> front, -> rear)

#### What is BubbleSort? Describe the main logic of this sorting algorithm.

A bubble-sort algorithm iterates through the given list, and compares each element's value to the next element's value. Given the list is to be sorted in ascending order, the algorithm switches the elements' places every time an element's value is greater than the value of the next element.

#### Explain the process of finding the maximum and minimum value in a list of numbers!

Iterate through the array and keep track of the actual highest / lowest number.

#### Explain the process of calculating the average value in an array of numbers!

Iterate through the array and return the sum of the numbers divided by the length of the array.

#### What is Big O complexity? Explain time and space complexity!

In computer science, big O notation is used to classify algorithms according to how their run time or space requirements grow as the input size grows.

Big O specifically describes the worst-case scenario, and can be used to describe the execution time required or the space used (e.g. in memory or on disk) by an algorithm.

- O(1) -- constant:
  Describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.
  `return elements[0] === null;`

- O(N) -- linear:
  Describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.

```javascript
for (let element of elements) {
  if (element === value) {
    return true;
  }
}
```

- O(N^2) -- quadratic:
  Represents an algorithm whose performance is directly proportional to the square of the size of the input data set. This is common with algorithms that involve **nested iterations** over the data set. Deeper nested iterations will result in O(N^3), O(N^4) etc.

- O(2^N):
  Denotes an algorithm whose growth doubles with each additon to the input data set. The growth curve of an O(2N) function is exponential - starting off very shallow, then rising meteorically.
  E.g. recursive calculation of **Fibonacci numbers**

- O(log N) -- logarithmic:
  E.g. **Binary Search**:
  Binary search is a technique used to search sorted data sets. It works by selecting the middle element of the data set, essentially the median, and compares it against a target value. If the values match it will return success. If the target value is higher than the value of the probe element it will take the upper half of the data set and perform the same operation against it. Likewise, if the target value is lower than the value of the probe element it will perform the operation against the lower half. It will continue to halve the data set with each iteration until the value has been found or until it can no longer split the data set.

  (The iterative halving of data sets described in the binary search example produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase e.g. an input data set containing 10 items takes one second to complete, a data set containing 100 items takes two seconds, and a data set containing 1000 items will take three seconds. Doubling the size of the input data set has little effect on its growth as after a single iteration of the algorithm the data set will be halved and therefore on a par with an input data set half the size. This makes algorithms like binary search extremely efficient when dealing with large data sets).

#### Explain the process of calculating the average value in a linked list of numbers!

Make a SUM variable. Because linked lists don't have indices, we have to make a counter. We go trough the list in a while loop and add its value to SUM, till the current element is NULL. Then we divide the SUM with the counter.

### Procedural

#### How the CASE condition works in SQL?

The PostgreSQL `CASE` expression is the same as if/else statement in other programming languages.

In this general form, each condition is an expression that returns a _boolean_ value, either true or false.
If the condition evaluates to true, the `CASE` expression returns the result corresponding to the condition and all other `CASE` branches do not process at all.
If all conditions evaluate to false, the `CASE` expression will return the result in the `ELSE` part. If you omit the `ELSE` clause, the `CASE` expression will return `NULL`.

```sql
SELECT title,
       rating,
       CASE rating
           WHEN 'G' THEN 'General Audiences'
           WHEN 'PG' THEN 'Parental Guidance Suggested'
           WHEN 'PG-13' THEN 'Parents Strongly Cautioned'
           WHEN 'R' THEN 'Restricted'
           WHEN 'NC-17' THEN 'Adults Only'
       END rating_description
FROM film
ORDER BY title;
```

#### How the switch-case condition works in JavaScript?

A switch statement can replace multiple `if` checks.
It gives a more descriptive way to compare a value with multiple variants.

```javascript
let a = 2 + 2;

switch (a) {
  case 3:
    alert("Too small");
    break;
  case 4:
    alert("Exactly!");
    break;
  case 5:
    alert("Too large");
    break;
  default:
    alert("I don't know such values");
}
```

#### How to achieve a switch-case-like structure in Python?

if-elif-else blocks

#### Explain variable scoping in Python!

Not all variables are accessible from all parts of our program, and not all variables exist for the same amount of time. Where a variable is accessible and how long it exists depend on how it is defined.
We call the part of a program _where_ a variable is accessible its **scope**, and the _duration_ for which the variable exists its **lifetime**.

A variable which is defined in the _main body_ of a file is called a _global variable_. It will be visible throughout the file, and also inside any file which imports that file. Global variables can have unintended consequences because of their wide-ranging effects – that is why we should almost never use them. Only objects which are intended to be used globally, like functions and classes, should be put in the global namespace.

A variable which is defined _inside_ a function is _local_ to that function. It is accessible from the point at which it is defined until the end of the function, and exists for as long as the function is executing. The parameter names in the function definition behave like local variables, but they contain the values that we pass into the function when we call it. When we use the assignment operator (`=`) inside a function, its default behaviour is to create a new local variable – unless a variable with the same name is already defined in the local scope.

#### What’s the difference between const and var in JavaScript?

`var`:

- function scoped
- `undefined` when accessing a variable before it's declared

`let`:

- block scoped
- `ReferenceError` when accessing a variable before it's declared

`const`:

- block scoped
- `ReferenceError` when accessing a variable before it's declared
- can't be reassigned (although data structures can be modified in-place)

Use `const` whenever you can. If the value will change, use `let` instead.

#### How the list comprehension looks like in Python?

`doubles_of_x = [x * 2 for x in elements]`

#### How the "ternary expression" looks like in Python?

`a if a < b else b`

#### How the ternary expression looks like in JavaScript?

`a < b ? a : b`

#### How to import a function from another module in Python?

`from module import function (as ...)`

#### How to import a function from another module in JavaScript?

`export function`

`import { function } from "./filename";`

### Functional

#### What is recursion?

A recursive function is a function defined in terms of itself via _self-referential expressions_. This means that the function will continue to call itself and repeat its behavior until some condition is met to return a result.

#### Write a recursive function which calculates the Fibonacci numbers!

```javascript
fibonacciNaiveRecursive = n => {
  if (n <= 1) return n;

  fib = fibonacciNaiveRecursive(n - 1) + fibonacciNaiveRecursive(n - 2);

  return fib;
};
```

#### How to store a function in a variable in Python?

`x = function_name`

#### List the ways of defining a callable logical unit in JavaScript!

`function myFunc () {}`

`const myFunc = function () {};`

`const myFunc = () => {};`

#### What is an event listener? How to attach one?

The `EventListener` interface represents an object that can handle an event dispatched by an `EventTarget` object.

```javascript
buttonElement.addEventListener('click', function (event) {
    event.target.style = color: red;
});
```

#### How to trigger an event in JavaScript?

Using standard DOM actions (e.g. click on the selected element).

In JS code: `element.dispatchEvent(event);`.

#### What is a callback function? Tell some examples of its usage.

A callback function is any executable code that is passed as an **argument** to other code that is expected to _call back_ (execute) the argument at a given time.

This execution may be _immediate_ as in a _synchronous_ callback, or it might happen at a _later_ time as in an _asynchronous_ callback:

- `setTimeout()`
- `setInterval()`
- API callbacks

#### What is a Python decorator? How does it work? Tell some examples of its usage.

Decorators add functionality to an existing code. This is also called _metaprogramming_ as a part of the program tries to modify another part of the program at _compile time_.

A decorator is a callable that returns a callable.

Basically, a decorator is a function that can run logic before and after the function it "decorates". It takes in the function, adds some functionality to it, and returns it.

```python
def make_pretty(func):
    def inner():
        print("I got decorated")
        func()
    return inner
```

In Flask's case, the framework can add request receiving logic before running your code, and figure out how to send it back to the user, after your logic.

#### What is the difference between synchronous and asynchronous execution?

When you execute something synchronously, you wait for it to finish before moving on to another task.

When you execute something asynchronously, you can move on to another task, and get the results when ready.

## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?

We need a database server, a connection/driver layer and a data connection from the Python side.
We connect to the server with a username-password, a hostname, and a DB name, in the form that the connection/driver layer expects. It usually also includes a port. This will give us an option to use a _cursor_ in python that we can use to execute _commands_ on the DB server.

#### When do you use the DISTINCT keyword in SQL?

The `SELECT DISTINCT` statement is used to return values that are distinct / unique.

#### What are aggregate functions in SQL? Give 3 examples.

`COUNT()`

`SUM()`

`AVG()`

#### What kind of JOIN types do you know in SQL? Could you give examples?

`(INNER) JOIN`:
Returns records that have matching values in both tables

`LEFT (OUTER) JOIN`:
Returns all records from the left table, and the matched records from the right table

`RIGHT (OUTER) JOIN`:
Opposite of the left outer join -- rarely used

`FULL (OUTER) JOIN`:
Returns all records when there is a match in either left or right table (cartesian product)

#### What are the constraints in sql?

SQL constraints are used to specify rules for data in a table.

Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:

- `NOT NULL`:
  Ensures that a column cannot have a NULL value
- `UNIQUE`:
  Ensures that all values in a column are different
- `PRIMARY KEY`:
  A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
- `FOREIGN KEY`:
  Uniquely identifies a row/record in another table
- `CHECK`:
  Ensures that all values in a column satisfies a specific condition
- `DEFAULT`:
  Sets a default value for a column when no value is specified
- `INDEX`:
  Used to create and retrieve data from the database very quickly

#### What is a cursor in SQL? Why would you use one?

A database cursor can be thought of as a _pointer_ to a specific row within a query result. The pointer can be moved from one row to the next.
Cursors let you perform actions on individual rows.

#### What are database indexes? When to use?

A database index allows a query to efficiently retrieve data from a database. Indexes are related to specific tables and consist of one or more keys.

The keys are based on the tables' columns. By comparing keys to the index it is possible to find one or more database records with the same value.

#### What are database transactions? When to use?

A transaction is a unit of work that you want to treat as "a whole". It has to either happen in full or not at all.

A classical example is transferring money from one bank account to another. To do that you have first to withdraw the amount from the source account, and then deposit it to the destination account. The operation has to succeed in full. If you stop halfway, the money will be lost.

In modern databases transactions also do some other things - like ensure that you can't access data that another person has written halfway. But the basic idea is the same - transactions are there to ensure, that no matter what happens, the data you work with will be in a sensible state.

A transaction, in the context of a database, is a logical unit that is independently executed for data retrieval or updates. In relational databases, database transactions must be atomic, consistent, isolated and durable--summarized as the **ACID** acronym.

- Atomicity:
  A transaction must be fully complete, saved (committed) or completely undone (rolled back). A sale in a retail store database illustrates a scenario which explains atomicity, e.g., the sale consists of an inventory reduction and a record of incoming cash. Both either happen together or do not happen - it's all or nothing.
- Consistency:
  The transaction must be fully compliant with the state of the database as it was prior to the transaction. In other words, the transaction cannot break the database's constraints. For example, if a database table's Phone Number column can only contain numerals, then consistency dictates that any transaction attempting to enter an alphabetical letter may not commit.
- Isolation:
  Transaction data must not be available to other transactions until the original transaction is committed or rolled back.
- Durability:
  Transaction data changes must be available, even in the event of database failure.

#### What kind of database relations do you know? How to define them?

One-to-One:

- A row in table "A" can have only one matching row in table "B", and vice versa.

One-to-Many (or Many-to-One):

- This is the most common relationship type.
- A row in table "A" can have many matching rows in table "B", but a row in table "B" can have only one matching row in table "A".

Many-to-Many:

- In a many-to-many relationship, a row in table "A" can have many matching rows in table "B", and vice versa.

#### You have a table with an "address" field which contains data like "3525, Miskolc, Régiposta 9." (postcode, city, street name and address). How would you query all records related to Miskolc?

`SELECT * FROM table WHERE city = 'Miskolc';`

`SELECT * FROM table WHERE address LIKE '%, Miskolc, %';`

#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?

In general, if your application is structured into layers, have the data access tier call a stored procedure on your database server to write a log of the database changes.

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?

XML and HTML were designed with different goals.

XML (Extensible Markup Language):

- Designed to _carry_ data - with focus on what data is.
- XML tags are not predefined like HTML tags are.

HTML (HyperText Markup Language):

- Designed to _display_ (present) data - with focus on how data looks.

XHTML:

- Is a family of XML markup languages that mirror or extend versions.

#### How to include a JavaScript file in a webpage?

Use the `<script>` tag that wraps around JavaScript code directly

Use an external JavaScript file by adding a link to it in the head or lower body section of the HTML document.

#### How to include a CSS file in a webpage?

Use an external style sheet by adding a link to it in the head section of the HTML document.

#### How to select an element using its id in CSS?

`#id`

#### How to select elements using their class in CSS?

`.class`

#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?

`.alpha.beta`

#### How to select all list items in all ordered lists on the page in CSS?

`ol li`

#### How to select elements using their attributes in CSS?

The `[attribute]` selector is used to select elements with a specified attribute.

The following example selects all `<a>` elements with a target attribute:

```css
a[target] {
  background-color: yellow;
}
```

#### What are UX and UI?

UX (User Experience):
Essentially, UX applies to anything that can be experienced — be it a website, a coffee machine, or a visit to the supermarket. The "user experience" part refers to the interaction between the user and a product or service.

UI (User Interface):
User interface (UI) is anything a user may interact with to use a digital product or service.

#### Please list some points that an application should fulfill to have good UX.

Visual Design:
From hypertext point of view, visual design is described as _visual_ treatment of the text, graphic page elements and navigational components.

Information Design:
Here (web applications), the information design is the process of designing the _presentation of information_ to facilitate understanding. From Hypertext System point of view, it can be described as Navigation Design (design of interface elements to facilitate the user's movement through the information architecture).

#### What is XML, XSLT, DTD?

With XSLT you can transform an XML document into HTML.

A DTD (Document Type Definition) defines the structure and the legal elements and attributes of an XML document.

#### What is the difference between HTML and XML?

See above

### Javascript

#### What is javascript?

JavaScript is a scripting or programming language that allows you to implement complex features on web pages — every time a web page does more than just sit there and display static information for you to look at — displaying timely content updates, interactive maps, animated 2D/3D graphics, scrolling video jukeboxes, etc. — you can bet that JavaScript is probably involved.

It is the third layer of the layer cake of standard web technologies (HTML - CSS - JS).

#### When to use AJAX? Bring examples of its usage.

**AJAX** stands for **Asynchronous JavaScript And XML** (Asynchronous JavaScript And JSON), and it describes a set of development techniques used for building websites and web applications.
A user's web browser doesn't need to reload an entire web page when only a small portion of content on the page needs to change.
An example of asynchronous updating is Google's "Google Suggest" feature. When you enter a search query into Google's search bar and the Google website automatically begins offering auto-complete options while you type.

#### What is DOM and how to manipulate it from Javascript?

The DOM is **an object-oriented representation of the web page**, which can be modified with a scripting language such as JavaScript.

A Web page is a document. This document can be either displayed in the browser window or as the HTML source. But it is the same document in both cases. The **Document Object Model (DOM)** -- a programming interface for HTML and XML documents -- represents that same document so it can be manipulated (structure, style, content). The DOM **represents the document as nodes and objects**. That way, programming languages can connect to the page.

The **DOM** is the way Javascript sees its containing pages' data. It is an object that includes how the HTML/XHTML/XML is formatted, as well as the browser state.

A DOM element is something like a DIV, HTML, BODY element on a page. You can add classes to all of these using CSS, or interact with them using JS.

We can select a DOM element and manipulate it form Javascript:

- change content of an element
- manage attributes of an element
- add a new element
- remove an element

#### What are events and how/why to use them in Javascript?

Events are actions or occurrences that happen in the system you are programming, which the system tells you about so you can respond to them in some way if desired. For example, if the user clicks a button on a webpage, you might want to respond to that action by displaying an information box.

HTML events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can "react" on these events.

An HTML event can be something the browser does, or something a user does.

Examples of HTML events:

- an HTML web page has finished _loading_
- an HTML input field was _changed_
- an HTML button was _clicked_

#### What is event bubbling/capturing? How would you use it?

When an event happens on an element, it first runs the handlers (event handlers) on it, then on its parent, then all the way up on other ancestors. The process is called "bubbling", because events "bubble" from the inner element up through parents like a bubble in the water.

A handler on a parent element can always get the details about where it actually happened.
The most deeply nested element that caused the event is called a target element, accessible as `event.target`.

Note the differences from `this`:

- `event.target` – is the "target" element that initiated the event, it doesn't change through the bubbling process.
- `this` / `event.currentTarget` – is the "current" element, the one that has a currently running handler on it.

#### What is JSON and how do we use it?

- **JSON** stands for **JavaScript Object Notation**.
- JSON is a lightweight format for storing and transporting data.
- JSON is often used when data is sent from a server to a web page.
- JSON is "self-describing" and easy to understand.

A common use of JSON is to read data from a web server, and display the data in a web page.
String containing JSON syntax -> `JSON.parse(myString)` -> use the new Javascript object

## Software engineering

### Version control

#### What type of branching strategy would you use?

The **Gitflow** workflow.

It relies on two long-lived branches and some short-lived ones. The permanent ones are the "master" and the "development." The state of "master" should always be pristine; it reflects the last "good", stable version that's in production.
The other long-lived branch is the "develop" or "development" branch.

Short lived branches can include:

- "feature" branches
- "release" branch
- "hotfix" branch

#### What would you do if you find a bug on the production code (master branch)?

Create a hotfix branch, merge the master branch into it, fix the bug, checkout master, then make a pull request.

#### How can you move changes from one branch to another in GIT?

Merge or rebase.

#### How does a VCS help with code reviews?

Code review is crucial, and shipping high-quality code is everyone's responsibility. A Pull Request review on GitHub lets you combine multiple inline comments and an overarching summary into a single package that gives readers a clear and consolidated view of your thoughts and recommendations.

#### What is your favorite git command? Why?

`git push origin master` - it feels good to finalize a contribution to the project.

#### What does remote/local mean in Git?

A remote URL is Git's fancy way of saying "the place where your code is stored." That URL could be your repository on GitHub, or another user's fork, or even on a completely different server.

Git local repository is the one on which we will make local changes, typically this local repository is on our computer.

### DevOps

#### Why is it good to use a package manager software?

A _package manager_ or _package-management system_ is a collection of software tools that _automates_ the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

A package manager deals with packages, distributions of software and data in archive files. Packages contain metadata, such as the software's name, description of its purpose, version number, vendor, checksum, and a list of dependencies necessary for the software to run properly. Upon installation, metadata is stored in a local package database. Package managers typically maintain a database of software dependencies and version information to prevent software mismatches and missing prerequisites.

#### Why is it good to use a virtual environment for a project?

Venv (`venv` module) is a tool for creating isolated Python environments.

It solves a very specific problem: it allows multiple Python projects that have different (and often conflicting ) requirements, to coexist on the same computer.

### Networks

#### What kind of HTTP status codes do you know?

1. 1xx: Informational - Communicates transfer protocol-level information.
2. 2xx: Success - Indicates that the client's request was accepted successfully.
3. 3xx: Redirection - Indicates that the client must take some additional action in order to complete their request. ("You got redirected").
4. 4xx: Client Error - This category of error status codes points the finger at clients.
5. 5xx: Server Error - The server takes responsibility for these error status codes.

#### What is a API?

An **API (Application Programming Interface)** is a gate (interface) in a software, that allows connectivity for the outside word. Usually one API endpoint lets you interact with one certain part of the given software.

#### What is REST API?

**REST** (**REpresentational State Transfer**) or RESTful is an architectural style used for web development. A set of principles that define how Web standards, such as HTTP and URIs, are supposed to be used.

REST is all about a client-server relationship, where server-side data are made available through representations of data in simple formats, often JSON and XML.

These are representations for resources, which are then potentially modifiable, with actions and relationships being made discoverable via a method known as **hypermedia**. Hypermedia is fundamental to REST, and is essentially just the concept of providing **links** to other resources.

The 5 key principles are:

1. Give every "thing" an ID (meaning every resource should have a URI)
2. Link things together
3. Use standard methods
4. Resources with multiple representations
5. Communicate statelessly

In short, if you make a RESTful API, you ensure other developers can understand the structure easily compared to creating endpoints without a standard.

> RESTful APIs are stateless backends.

> The emphasis is on that we don't have to get back a new page (HTML document) after every request -- only data (JSON etc).

> Many of these API endpoints are not going to get targeted directly by the browser. The user won't enter any of these URLs.

RESTful constraints:

- Client-Server Architecture:
  - Separation of Concerns: RESTful API should not care about the UI
- Stateless:
  - No Client-Context (e.g. Session) is stored on the Server
- Cacheability:
  - Responses must define themselves as cacheable or non-cacheable
- Layered System:
  - Intermediate Servers may be used without the Client knowing about it
- Uniform Interface:
  - Resources are identified in Requests, transferred data is decoupled from DB schema
  - Self descriptive Messages
  - Links to further Resources
- Code on Demand (optional):
  - Executable Code could be transferred
  - Meaning it doesn't have to be just Data, it could be Code that the Client can execute

#### What is JSON? When to use?

See above

#### What is TCP/IP? What layers does it define, what are they responsible for?

**TCP/IP**, or the **Transmission Control Protocol/Internet Protocol**, is a suite of communication protocols used to interconnect network devices on the internet. TCP/IP can also be used as a communications protocol in a private network (an intranet or an extranet).

The first layer is the application layer on the behalf of the sender and Link layer on the behalf of the receiver.

**Link layer (Network Access layer, Physical layer)**:

- Looks out for **hardware addressing**, and the protocols present in this layer allows for the **physical transmission of data**.
- The protocols in this layer include:
  - **Ethernet** for local area networks (LANs)
  - Wi-Fi
  - DSL
  - ARP (Address Resolution Protocol)

**Internet layer (Network layer)**:

- Deals with **packets** and connects independent networks to transport the packets across network boundaries.
- The network layer protocols are:
  - **IP (Internet Protocol)** -- IPv4, IPv6
  - ICMP (Internet Control Message Protocol), which is used for error reporting

**Transport layer**:

- Responsible for **maintaining end-to-end communications** across the network. TCP handles communications between hosts and provides flow control, multiplexing and reliability.
- The transport protocols include:
  - **TCP (Transmission Control Protocol)**
  - **UDP (User Datagram Protocol)**
  - etc

**Application layer**:

Provides applications with **standardized data exchange**. Its protocols include:

- **DNS (Domain Name System)**
- **HTTP** (**Hypertext Transfer Protocol**) / HTTPS (Hypertext Transfer Protocol Secure)
- **TLS**/SSL (**Transport Layer Security** / Secure Sockets Layer) = ENCRYPTION PROTOCOL or CRYPTOGRAPHIC PROTOCOL
- **FTP** (**File Transfer Protocol**)
- **POP3** (**Post Office Protocol 3**)
- IMAP (Internet Message Access Protocol)
- SMTP (Simple Mail Transfer Protocol)
- Telnet
- etc.

#### What’s the difference between TCP and UDP?

TCP and UDP are the most commonly used protocols in the _TCP/IP model's_ Transportation layer. TCP is a _connection-based_ protocol and UDP is a _connection-less_ protocol, meaning: TCP establishes a connection between a sender and receiver before data can be sent. UDP does not establish a connection before sending data.

**TCP (Transmission Control Protocol)**:
TCP is a **connection-based** protocol that provides a reliable flow of data between two computers. When two applications want to communicate to each other reliably, they **establish a connection** (TCP/IP three-way handshake) and send data back and forth over that connection. TCP guarantees that data sent from one end of the connection actually gets to the other end and in the **same order it** was sent. Otherwise, an error is reported.

The Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), and Telnet are all examples of applications that require a reliable communication channel. The order in which the data is sent and received over the network is critical to the success of these applications. When HTTP is used to read from a URL, the data must be received in the order in which it was sent. Otherwise, you end up with a jumbled HTML file, a corrupt zip file, or some other invalid information.

> A TCP connection is analogous to **making a telephone call**. If you want to speak to Aunt Beatrice in Kentucky, a connection is established when you dial her phone number and she answers. You send data back and forth over the connection by speaking to one another over the phone lines.

**UDP (User Datagram Protocol)**:
UDP is a **connection-less** protocol that sends **independent packets of data**, called **datagrams**, from one computer to another with **no guarantees about arrival**.

For many applications, the guarantee of reliability is critical to the success of the transfer of information from one end of the connection to the other. However, other **forms of communication don't require such strict standards**. In fact, they **may be slowed down** by the extra overhead or the reliable connection may invalidate the service altogether.

> Sending datagrams is much like **sending a letter through the mail service**: The order of delivery is not important and is not guaranteed, and each message is independent of any others.

An example: ping. The purpose of the **ping command** is to test the communication between two programs over the network. In fact, ping needs to know about dropped or out-of-order packets to determine how good or bad the connection is. A reliable channel would invalidate this service altogether.

> Ping is a computer network administration software utility used to test the reachability of a host on an Internet Protocol (IP) network. Ping time is the network latency between a player's client and the game server as measured with the ping utility or equivalent.

#### How does an HTTP Request look like? What are the most relevant HTTP header fields?

**HTTP MESSAGES** IN GENERAL

HTTP messages are how data is exchanged between a server and a client. There are two types of messages: requests sent by the client to trigger an action on the server, and responses, the answer from the server.

HTTP requests, and responses, share similar structure and are composed of:

1. A **start-line** describing the requests to be implemented, or its status of whether successful or a failure. This start-line is always a single line.
2. An _optional_ set of **HTTP headers** specifying the request, or describing the body included in the message.
3. A **blank line** indicating all meta-information for the request has been sent.
4. An _optional_ **body**: containing data associated with the request (like content of an HTML form), or the document associated with a response. (The presence of the body and its size is specified by the start-line and HTTP headers).

The _start-line_ and _HTTP headers_ of the HTTP message are collectively known as the **head** of the requests, whereas its _payload_ is known as the **body**.

**Headers**:

- **General headers** apply to both requests and responses, but with no relation to the data transmitted in the body. The most common ones:
  - `Date`: Contains the date and time at which the message was originated. (E.g. _Date: Wed, 21 Oct 2015 07:28:00 GMT_).
  - `Cache-Control`: Holds directives (instructions) for caching in both requests and responses. A given directive in a request does not mean the same directive should be in the response.
  - `Connection`: Controls whether or not the network connection stays open after the current transaction finishes. If the value sent is keep-alive, the connection is persistent and not closed, allowing for subsequent requests to the same server to be done. (E.g. _Connection: keep-alive_, _Connection: close_).
  - `Via`: Included by intermediary devices to indicate to the recipient what gateways, proxies and/or tunnels were used in conveying a request or response. This header allows easy tracing of the path a message took over a potentially complex chain of devices between a client and server.
- **Request headers** allow a client to provide information about itself to a server, and provide more _details about a request_, and _control over how it is carried out_. The most important ones:
  - `Host`: Specifies the domain of the server it is communicating with. **Mandatory in HTTP/1.1 requests**, and if it is omitted then a `400` response will be triggered.
  - `Referer`: Tells the server where the requested URL came from. It will almost always be another URL, or else empty for a direct request (for example, the requester typed the URL into a browser address bar). (E.g. _Referer: https://www.quora.com/profile/Lee-Dowthwaite_). Fun fact: "referer" will persist forever in this misspelled state.
  - `User-Agent`: Identifies the **requesting system**. It is a string composed of a sequence of so-called _product tokens_ with optional comments. (E.g. _User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36_). Fun fact: All UA headers start with Mozilla 5.0 because of historical reasons (IE had to fake being Mozilla, and so others followed).
  - `Accept`: The Accept header is how a **client** (browser or application) tells the server **what kind of content it can accept** in the HTTP response. The content types are comma-separated, and take the form **type/subtype** (MIME types) such as text/html, application/json or audio/mpeg. Asterisks can be used as wildcards in place of either type or subtype. (E.g. _Accept: application/graphql, application/json; q=0.8, application/xml; q=0.7_).
  - `Authorization`: Extremely important for any website or application that requires **authorization of the user** before allowing access to resources (Basic, Bearer, Digest).
  - `Cookie`: Contains stored HTTP cookies previously sent by the server with the `Set-Cookie` header. (E.g. _Cookie: PHPSESSID=298zf09hf012fh2; csrftoken=u32t4o3tb3gg43; \_gat=1_).
- **Response headers** give additional information about the server which doesn't fit in the status line. Some important ones:
  - `Server`: This is the server's version of the `User-Agent` request header; it identifies the type and version of the server software generating the response. (E.g. _Server: Apache/2.4.1 (Unix)_).
  - `Location`: Indicates the URL to redirect a page to. It only provides a meaning when served with a 3xx (redirection) or 201 (created) status response.
  - `Vary`: Determines how to match future request headers to **decide whether a cached response can be used** rather than requesting a fresh one from the origin server. Example: when using the _Vary: User-Agent_ header, caching servers should consider the user agent when deciding whether to serve the page from cache. For example, if you are serving different content to mobile users, it can help you to avoid that a cache may mistakenly serve a desktop version of your site to your mobile users.
  - `Set-Cookie`: Used to **send a cookie from the server to the user agent**, so the user agent can send it back to the server later. To send multiple cookies, multiple Set-Cookie headers should be sent in the same response. (E.g. _Set-Cookie: id=a3fWa; Expires=Wed, 21 Oct 2015 07:28:00 GMT_).
- **Entity headers** contain information about the **body** of the resource. Key concept: HTTP entity headers appear in either request or response messages that carry an entity in the message body. They describe the nature of the entity, including its type, language and encoding, to facilitate the proper processing and presentation of the entity by the device receiving it.
  - `Content-Type`: Indicates the media type (MIME type) of the resource. (E.g. _Content-Type: text/html; charset=UTF-8_, _Content-Type: multipart/form-data; boundary=something_).
  - `Content-Length`: Indicates the **size** of the entity-body, in bytes, sent to the recipient.
  - `Transfer-Encoding`: ...
  - `Content-Language`: Describes the **language(s) intended for the audience**, so that it allows a user to differentiate according to the users' own preferred language. (E.g. _Content-Language: en-US_).
  - `Content-Encoding`: Used to compress the media-type. (E.g. _Content-Encoding: gzip_).

**HTTP REQUESTS**

HTTP requests are messages sent by the client to initiate an action on the server.

**Start-line**:

1. An **HTTP method**, a verb (like `GET`, `PUT` or `POST`) or a noun (like `HEAD` or `OPTIONS`), that describes the action to be performed. For example, `GET` indicates that a resource should be fetched or `POST` means that data is pushed to the server.
2. The request **target** (URI), usually a URL.
3. The **HTTP version**, which defines the structure of the remaining message.

A typical start-line looks like this: `GET http://developer.mozilla.org/en-US/docs/Web/HTTP/Messages HTTP/1.1`

**Headers**:

- **General headers**, such as `Date`, `Cache-Control`, `Connection`, `Via`.
- **_Request_ headers** such as `Host`, `Referer`, `User-Agent`, `Accept`, `Authorization`, `Cookie`.
- **Entity headers**, such as `Content-Type`, `Content-Length`, `Transfer-Encoding`, `Content-Language`, `Content-Encoding`.

**Body**:

- The final part of the request is its body. Not all requests have one: requests fetching resources, like `GET` or `DELETE`, usually don't need one. Some requests send data to the server in order to update it: as often the case with **`POST` requests** (containing HTML form data).
- Bodies can be broadly divided into two categories:
  - **Single-resource bodies**, consisting of **one single file**, defined by the 2 headers: `Content-Type` and `Content-Length`.
  - **Multiple-resource bodies**, consisting of a multipart body, each containing a different bit of information. This is typically associated with **HTML Forms**.

#### How does an HTTP Response look like? What are the most relevant HTTP header fields?

**Status line** (the start line of an HTTP response):

1. The **HTTP version**, usually `HTTP/1.1`.
2. A **status code**, indicating success or failure of the request. Common status codes are `200`, `404`, or `302`
3. A **status text**. A brief, purely informational, textual description of the status code to help a human understand the HTTP message.

A typical status line looks like: `HTTP/1.1 404 Not Found`.

**Headers**:

- **General headers**, such as `Date`, `Cache-Control`, `Connection`, `Via`.
- **_Response_ headers**, such as `Server`, `Location`, `Vary`, `Set-Cookie`.
- **Entity headers**, such as `Content-Type`, `Content-Length`, `Transfer-Encoding`, `Content-Language`, `Content-Encoding`.

**Body**:

- The last part of a response is the body. Not all responses have one: responses with a status response, like `201 Created` or `204 No Content`, usually don't.
- **Single-resource bodies**, consisting of a **single file of _known_ length**, defined by the two headers: `Content-Type` and `Content-Length`.
- Single-resource bodies, consisting of a **single file of _unknown_ length**, encoded by chunks with `Transfer-Encoding` set to `chunked`. For example, a **YouTube video** or any other **stream**.
- Multiple-resource bodies, consisting of a multipart body, each containing a different section of information. These are relatively rare.

#### What is DNS? How does it work?

The **Domain Name System (DNS)** is the **phonebook of the Internet**. When users type domain names such as 'google.com' or 'nytimes.com' into web browsers, DNS is responsible for finding the correct IP address for those sites. Browsers then use those addresses to communicate with origin servers or CDN edge servers to access website information. This all happens thanks to **DNS servers**: machines dedicated to answering **DNS queries**.

#### What is a web server?

"Web server" can refer to hardware or software, or both of them working together:

- On the **hardware** side, a web server is a computer that stores web server software and a website's component files (e.g. HTML documents, images, CSS stylesheets, and JavaScript files). It is connected to the Internet and supports physical data interchange with other devices connected to the web.
- On the **software** side, a web server includes several parts that control how web users access hosted files, at minimum an HTTP server.

An **HTTP server** is a piece of software that understands URLs and HTTP. It can be accessed through the domain names (like mozilla.org) of websites it stores, and delivers their content to the end-user's device.

To publish a website, you need either a static or a dynamic web server:

- A **static web server**, or stack, consists of a computer (hardware) with an HTTP server (software). We call it "static" because the server sends its hosted files "as-is" to your browser.
- A **dynamic web server** consists of a static web server plus extra software, most commonly an **application server** and a **database**. We call it "dynamic" because the application server updates the hosted files before sending them to your browser via the HTTP server.

#### Explain the client-server architecture.

Client/server architecture is a computing model in which the server hosts, delivers and manages most of the resources and services to be consumed by the client. This type of architecture has one or more client computers connected to a central server over a network or internet connection. This system shares computing resources.

#### What would you use a session for?

Because HTTP is stateless, in order to associate a request to any other request, you need a way to store user data between HTTP requests.

Cookies or URL parameters (like http://example.com/myPage?asd=yes&boo=2) are both suitable ways to transport data between 2 or more request. However they are not good in case you don't want that data to be readable/editable on the client side.

The solution is to store that data server side, give it an "id", and let the client only know (and pass back at every http request) that id. There you go, sessions implemented. Or you can use the client as a convenient remote storage, but you would encrypt the data and keep the secret server-side.

#### What would you use a cookie for?

Using the **Set-Cookie** header field, an HTTP server can pass **name/value pairs and associated metadata** (called cookies) to a **user agent**. When the user agent makes subsequent requests to the server, the user agent uses the metadata and other information to determine whether to return the name/value pairs in the Cookie header.

An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with later requests to the same server. Typically, it's used to tell if two requests came from the same browser — keeping a user logged-in, for example. It **remembers stateful information** for the stateless HTTP protocol.

Cookies are mainly used for 3 purposes:

- **Session management**: Logins, shopping carts, game scores, or anything else the server should remember.
- **Personalization**: User preferences, themes, and other settings.
- **Tracking**: Recording and analyzing user behavior. This is how ads follow you.

Contains a name/value pair plus optional metadata (key/value pairs):

- expiration date: `expires=` or `max-age=`
- domain: `domain=`
- path: `path=`
- https security: `Secure`
- http only: `HttpOnly`

Cookie alternatives: There is a technology that recently got popular, called **JSON Web Tokens (JWT)**, which is a **Token-based Authentication**.

> Cookies are essentially used to store a session id.

> Cookies can only store 4KB of data.

## Software Development Methodologies

#### What kind of software development methodologies do you know? What are the main features of these?

In original **waterfall model**, the following phases are followed in order:

1. System and software **requirements**: captured in a product requirements document
2. **Analysis**: resulting in models, schema, and business rules
3. **Design**: resulting in the software architecture
4. **Coding**: the development, proving, and integration of software
5. **Testing**: the systematic discovery and debugging of defects
6. **Operations**: the installation, migration, support, and maintenance of complete systems

Thus the waterfall model maintains that one should move to a phase only when its preceding phase is reviewed and verified.

**Agile** project management:

- Agile is a time boxed, iterative approach to software delivery that builds software incrementally from the start of the project, instead of trying to deliver it all at once near the end.

#### What are the SCRUM roles?

Scrum Master:

- The team's coach, and helps Scrum practitioners achieve their highest level of performance.
- In the Scrum process, a Scrum Master differs from a traditional project manager in many ways, including that this role does not provide day-to-day direction to the team and does not assign tasks to individuals.
- A good Scrum Master shelters the team from outside distractions, allowing team members to focus maniacally during the sprint on the goal they have selected.

Product Owner:

- While the Scrum Master focuses on helping the team be the best that it can be, the product owner works to direct the team to the right goal. The product owner does this by creating a compelling vision of the product, and then conveying that vision to the team through the product backlog.
- Responsible for prioritizing the backlog during Scrum development, to ensure it's up to par as more is learned about the system being built, its users, the team and so on.

Scrum Team:

- Although individuals may join the team with various job titles, in Scrum, those titles are insignificant. Scrum methodology states that each person contributes in whatever way they can to complete the work of each sprint.
- This does not mean that a tester will be expected to re-architect the system; individuals will spend most (and sometimes all) of their time working in whatever discipline they worked before adopting the agile Scrum model. But with Scrum, individuals are expected to work beyond their preferred disciplines whenever doing so would be for the good of the team.

#### What are the SCRUM ceremonies?

1. Sprint Planning:
   This is where the team meets and decides what they need to complete in the coming sprint.

2. Daily Scrum / Daily Standup:
   This is a standup meeting, or a very short – 15-minute mini-meeting – for the team to make sure they're all on the same page.

3. Sprint Review:
   This is another type of meeting, but one in which the team demos what they shipped in the sprint.

4. Sprint Retrospective:
   This is when the team reviews their work, identifying what they did well and what didn't go as planned, so they can make the next sprint better.

#### What are the SCRUM artifacts?

Scrum's artifacts represent work or value to provide transparency and opportunities for inspection and adaptation. Artifacts defined by Scrum are specifically designed to maximize transparency of key information so that everybody has the same understanding of the artifact.

The Scrum Artifacts are:

1.  Product Backlog:

- An ordered list of everything that is known to be needed in the product. It is the single source of requirements for any changes to be made to the product. The Product Owner is responsible for the Product Backlog, including its content, availability, and ordering.

2.  Sprint Backlog:

- The set of Product Backlog items selected for the Sprint, plus a plan for delivering the product Increment and realizing the Sprint Goal.
- A forecast by the Development Team about what functionality will be in the next Increment and the work needed to deliver that functionality into a "Done" Increment.

3. Increment:

- The sum of all the Product Backlog items completed during a Sprint and the value of the increments of all previous Sprints.
- At the end of a Sprint, the new Increment must be "Done", which means it must be in useable condition and meet the Scrum Team's definition of "Done".
- Although this may vary significantly per Scrum Team, members must have a shared understanding of what it means for work to be complete, to ensure transparency. This is the definition of "Done" for the Scrum Team and is used to assess when work is complete on the product Increment.

#### What is the main goal of a retrospective meeting?

The goal of the retrospective is for the team members to discuss among themselves about how the work went during the last sprint so that better ways can be found to meet the project's goals. This means the team should talk about its internal processes as well.

#### Explain, when would you recommend to use the waterfall methodology?

The waterfall development model originates in the manufacturing and construction industries: highly structured physical environments in which after-the-fact changes are prohibitively costly, if not impossible.

## Bonus

### General

#### What happens when you type a URL in the browser and press enter?

1. You type maps.google.com into the address bar of your browser and **press ENTER**.
2. The **browser checks the cache for a DNS record** to find the corresponding IP address of maps.google.com.
   - To find the DNS record, the browser checks 4 caches:
     1. First, it checks the **browser cache**. The browser maintains a repository of DNS records for a fixed duration for websites you have previously visited. So, it is the first place to run a DNS query.
     2. Second, the browser checks the **OS cache**. If it is not in the browser cache, the browser will make a system call (i.e., gethostname on Windows) to your underlying computer OS to fetch the record since the OS also maintains a cache of DNS records.
     3. Third, it checks the **router cache**. If it's not on your computer, the browser will communicate with the router that maintains its own cache of DNS records.
     4. Fourth, it checks the **ISP cache**. If all steps fail, the browser will move on to the ISP. Your ISP maintains its own DNS server, which includes a cache of DNS records, which the browser would check with the last hope of finding your requested URL.
3. If the requested URL is not in the cache, **ISP's DNS server initiates a DNS query** to find the IP address of the server that hosts maps.google.com.
   - The purpose of a DNS query is to search multiple DNS servers on the internet until it finds the correct IP address for the website. This type of search is called a **recursive search** since the search will repeatedly continue from a DNS server to a DNS server until it either finds the IP address we need or returns an error response saying it was unable to find it.
   - If all goes well, the browser gets back the correct **IP address**.
4. The browser initiates a **TCP connection** with the server.
   - Once the browser receives the correct IP address, it will build a connection with the server that matches the IP address to transfer information -- using TCP in this case (and most other cases).
   - To transfer **data packets** between your computer (client) and the server, a TCP connection is established using a process called the **TCP/IP three-way handshake**. This is a three-step process where the client and the server **exchange SYN (synchronize) and ACK (acknowledge) messages** to establish a connection:
     1. The client machine sends a **SYN packet** to the server over the internet, asking if it is open for new connections.
        _client_ --SYN--> _server_
     2. If the server has open ports that can accept and initiate new connections, it'll respond with an ACKnowledgment of the SYN packet using a **SYN/ACK packet**.
        _client_ <--SYN/ACK-- _server_
     3. The client will receive the SYN/ACK packet from the server and will acknowledge it by sending an **ACK packet**.
        _client_ --ACK--> _server_
   - Then a TCP connection is established for data transmission!
5. The browser sends an **HTTP request** to the webserver.
   - The browser will send a **GET request** asking for maps.google.com web page.
   - This request will also contain additional information such as:
     - browser identification (**User-Agent** header)
     - types of requests that it will accept (**Accept** header)
     - connection headers (**Connection** header, like _Connection: Keep-Alive_) asking it to keep the TCP connection alive for additional requests
   - It will also pass information taken from **cookies** the browser has in store for this domain.
6. The server **handles the request**.
   - The server contains a **webserver** (i.e., Apache, IIS) that receives the request from the browser and passes it to a _request handler_ to read and generate a response.
   - The **request handler** is a program (written in ASP.NET, PHP, Ruby, etc.) that reads the request, its headers, and cookies to check what is being requested and also update the information on the server if needed. Then it will **assemble a response in a particular format** (JSON, XML, HTML).
7. The server sends out an **HTTP response**.
   - The server response contains the **web page you requested** as well as the **status code**, compression type (Content-Encoding), how to cache the page (Cache-Control), **any cookies to set**, privacy information, etc.
   - Status codes:
     - **1xx** indicates an informational message only
     - **2xx** indicates success of some kind
     - **3xx** redirects the client to another URL
     - **4xx** indicates an error on the client's part
     - **5xx** indicates an error on the server's part
8. The browser **displays the HTML content** (for HTML responses, which is the most common).
   - The browser displays the HTML content in phases.
   - First, it will **render the bare bone HTML skeleton**.
   - Then it will check the HTML tags and **send out GET requests for additional elements** on the web page, such as images, CSS stylesheets, JavaScript files, etc. These static files are **cached by the browser**, so it doesn't have to fetch them again the next time you visit the page.
   - In the end, you'll see maps.google.com appearing on your browser.
