# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
The list is the most versatile compound data type. It can be indexed and sliced, and since it's a mutable type, its contents can be changed as needed. Nested lists can be useful for representing matrices or similar constructs.

List methods:
    list.append(x):
        Add an item to the end of the list. Equivalent to a[len(a):] = [x].
    list.extend(iterable):
        Extend the list by appending all the items from the iterable. Equivalent to a[len(a):] = iterable.
    list.insert(i, x):
        Insert an item at a given position. The first argument is the index before which to insert. a.insert(len(a), x) is equivalent to a.append(x).
    list.remove(x):
        Remove the first item from the list whose value is equal to x.
    list.pop(i=optional):
        Remove the item at the given position in the list, and return it. If no index is specified, a.pop() removes and returns the last item in                    the list.
    list.clear():
        Remove all items from the list. Equivalent to del a[:].
    list.index(x, start=optional, end=optional):
        Return index in the list of the first item whose value is equal to x. The optional arguments start and end are interpreted as in the slice notation and are used to limit the search to a particular subsequence of the list. The returned index is computed relative to the beginning of the full sequence rather than the start argument.
    list.count(x):
        Return the number of times x appears in the list.
    list.sort(key=None, reverse=False):
        Sort the items of the list in place.
    list.reverse():
        Reverse the elements of the list in place.
    list.copy():
        Return a shallow copy of the list. Equivalent to a[:].


#### What is the difference between a list/array and a set?
A set is an (mutable,) unordered collection with no duplicate elements. Basic uses include membership testing and eliminating duplicate entries. Sets are not iterable.
Sets, (unlike lists) support mathematical operations like
    union:                  a | b   # letters in a or b or both
    intersection:           a & b   # letters in both a and b
    difference:             a - b   # letters in a but not in b
    symmetric difference:   a ^ b   # letters in a or b but not both


#### What is the purpose and methods of a dictionary/map data structure?
The dictionary is a mutable data type. Dictionaries are indexed by keys, which can be any immutable type. Strings and numbers can always be keys. Tuples can be used as keys if they contain only strings, numbers or tuples; if a tuple contains any mutable object either directly or indirectly, it cannot be used as a key.
A dictionary is a set of key-value pairs, with the requirement that the keys are unique (within one dictionary).
The main operations on a dictionary are storing a value with some key and extracting the value given the key. It is also possible to delete a key-value pair with the del statement. If you store a value using a key that is already in use, the old value associated with that key is forgotten.

Dictionary methods:
    list(d):
        Return a list of all the keys in the dictionary, in insertion order.
    sorted(d):
        Return a list of all the keys in the dictionary, in a specified order.
    
    dict.clear():
        Remove all the elements from the dictionary.
    dict.copy():
        Return a copy of the dictionary.
    dict.get(k):
        Return the value of the specified key k.
    dict.keys():
        Return a list containing the dictionary's keys.
    dict.values():
        Return a list of all the values in the dictionary.
    dict.items():
        Return a list containing a tuple for each key-value pair.
    dict.pop(k):
        Remove and return the element with the specified key k.
    dict.popitem():
        Remove and return a tuple of the last inserted key-value pair.
    dict.setdefault(k, v):
        Return a value of the specified key k. If the key does not exist, insert the key with the specified value v.
    dict.update({k: v, k: v, ...}):
        Update the dictionary with the specified key-value pairs. If a key already extists, the old value associated with that key is forgotten.
    dict.fromkeys(x, y):
        Return a dictionary with the specified keys and values. Here, x could represent a list ['key1', 'key2', ...] of keys, y could represent an integer value 1.


### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
def fibonacci(x, y):
    z = x + y
    print(z)
    fibonacci(y, z)


#### How do you find a max value in a list/array if you can’t use any built-in functions?
def get_max(numbers):
    i = 0
    counter = 0
    while counter < len(numbers):
        counter = 0
        for _ in numbers:
            if numbers[i] > numbers[i + 1]:
                numbers[i], numbers[i + 1] = numbers[i + 1], numbers[i]
            else:
                if i < len(numbers) - 2:
                    i += 1
                    counter += 1
                else:
                    i = 0
                    counter += 1

    return numbers


#### How do you find the average of values in a list/array if you can’t use any built-in functions?
def get_average(numbers):
    summa = 0
    i = 0
    counter = 0
    while counter < len(numbers):
        counter = 0
        for _ in numbers:
            summa += numbers[i]
            if i < len(numbers) - 1:
                i += 1
                counter += 1
            else:
                i = 0
                counter += 1

    average = summa / len(numbers)

    return average


#### What do we call an *in-place* sort?
A method like list.sort() modifies the object (rather than create and modify a new one).

#### Explain an algorithm which sorts a list!
A bubble-sort algorithm iterates through the given list, and compares each element's value to the next element's value. Given the list is to be sorted in ascending order, the algorithm switches the elements' places every time an element's value is greater than the value of the next element.


### Programming paradigms - procedural

#### What is the call stack?
The call stack is a dynamic data structure, maintained inside the computer's RAM by the operating system. Its purpose is to control the way procedures and functions call each other, and to control the way they pass parameters to each other. A call stack is maintained for each task, and each thread.


#### What is “Stack overflow”?
A stack overflow occurs if the call stack pointer exceeds the stack bound. The call stack may consist of a limited amount of address space, often determined at the start of the program. The size of the call stack depends on many factors, including programming language, machine (CPU) architecture, multi-threading, and amount of available memory. When a program attempts to use more space than is available on the call stack (that is, when it attempts to access memory beyond the call stack's bounds, which is essentially a buffer overflow), the stack is said to overflow, typically resulting in a program crash.
Common causes of stack overflow: excessively deep or infinite recursion, very large stack variables.


#### What are the main parts of a function?
A function head that defines the function, and the function body that contains the function's logic.

Function Head:
    def statement
    function name
    parentheses (if there are parameters, containing those)

Function Body:
    statements
    expressions
    arguments
    variables
    (function calls, parameters)


### Programming languages - Python

#### How do you use a dictionary in Python?
dict = {'first key': 1, 'second key': 2, 'third key': 3}


#### What does it mean that an object is immutable in Python?
Immutable objects cannot be modified in-place.


#### What is conditional expression in Python?
A conditional statement results in a defined outcome when a certain condition is met (the expression's Boolean value is True).
Conditional expressions:
    if
    elif
    else


#### What are different types of arguments in Python?
Default arguments:
Keyword arguments:
Variable-length arguments:


#### What is variable shadowing? (context: variable scope)
Variable shadowing occurs when a variable declared in a certain scope has the same name as a variable declared in an outer scope. This outer variable is said to be shadowed by the inner variable, while the inner identifier is said to mask the outer identifier.
If this happens, it can be confusing, but the program runs fine.


#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
If you delete/drop an item from a list while iterating over it, the results will be inaccurate. Due to the changed contents (indices), the loop will skip some elements and/or end prematurely. If we add to the list while iterating over it, it could result in an infinite loop.


#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
LEGB stands for
    Local: Defined inside function/class.
    Enclosed: Defined inside enclosing functions (nested functions concept).
    Global: Defined at the uppermost level.
    Built-in: Reserved names in Python built-in modules.
LEGB is the hierarchy in which python looks for variables (and functions as well).
Variables have different lifetimes, depending on their definition. E.g. a local variable exists as long as the function (in which it is defined) is being executed.
The golden rule means that variables should only be accessible where they are used. Avoiding using global variables as much as possible is standard.


#### If you need to access the iterator variable after a for loop, how would you do it in Python?
I can simply use the iterator variable after the loop has ended.


#### What type of elements can a list contain in Python?
Lists can contain any built-in data type.


#### What is slice operator in Python and how to use?
Using a slice operator does not change the list in-place but creates a new object.
list[start:end:step] (the end index is non-inclusive)
    list[:] - Creates a new (independent) copy of the list. Modifying this list won't affect the original list.
    list[::-1] - Reverses the list.


#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
The + operator concatenates list b to list a. (In other words, it appends list b's elements to list a's elements).
The * operator multiplies a list's elements by an integer.
The - and / operators are unsupported and result in an error.


#### What is the purpose of the in and not in membership operators in Python?
Membership operators are operators used to validate the membership of a value. It tests for membership in a sequence (such as strings, lists, or tuples).
    in: Evaluates to True if the specified object exists in the specified sequence, evaluates to False otherwise.
    not in: Reverse of the in operator.
    is: Evaluates to True if the variables on either side of the operator point to the same object, and False otherwise.
    is not: Reverse of the is operator.


#### What does the + operator mean when used with strings in Python?
The + operator concatenates string b to string a.


#### Explain f strings in Python?
f("{variable}")
Also called "formatted string literals", the f-string is a new and improved way to format strings in Python. It is a string literal that has an f at the beginning and curly braces containing expressions that will be replaced with their values. The expressions are evaluated at runtime and then formatted using the _format_ protocol.


#### Name 4 iterable types in Python!
String
List
Tuple
Dictionary


#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
List/set/dictionary comprehensions create the entire collection at once, while generators can evaluate elements on demand. The yield statement "saves" the state of the function (rather than terminating it as the return statement) and can be used when the generator is called again. Generators are slower but use less memory.


#### Does the order of the function definitions matter in Python? Why?
What matters is that we declare all functions that interact with each other before we call any of them (because they get executed only when called).


#### What does unpacking mean in Python?
Functions can use the elements of an "unpacked" collection as parameters.
(*my_list)
(*my_tuple)
(*my_set)
(**my_dict)


#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
None is assigned as a result.


## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
You can use doctest, a linter (PEP8), the print() statement (poor man's debugger), and the Debug tool in VS Code.


#### What does step over, step into and step out mean while using the debugger?
Step over: Steps over a line. If the line is a function, it gets executed and returned in the debug menu.
Step into: Steps into the next function and continue debugging there.
Step out: Returns to the line where the function was called.


#### How can you start to debug a program from a certain line using the debugger?
By putting a breakpoint into that line. The program will run up to the breakpoint, and start debugging from there.

### Version control

#### What are the advantages of using a version control system?
You can record and follow every change throughout the project. Multiple people can work on the same code at the same time. If something goes wrong, you can always go back to a previous version.


#### What is the difference between the working directory, the staging area and the repository in git?
Working directory: Contains the files that are untracked by Git (still "in the works").
Staging area: Contains the files that are added from the working directory. Git keeps track of any change that happens to these files.
Local git repository: The .git/ directory inside a project. Contains the files that are pushed from the staging area. This repository tracks all changes made to files in your project, building history over time. If you delete the .git/ folder, you destroy your whole project's history.


#### What are remote repositories in git?
Remote repositories store all the versions of a project in the cloud, e.g. GitHub.


#### Why does a merge conflict occur?
Merge conflicts occur when competing changes are made to the same line of a file, or when one person edits a file and another person deletes the same file.


#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
touch new_file
git add new_file
git commit -m "Add new file"
git push origin master


#### What does it mean atomic commits and descriptive commit messages?
Atomic commits: When you commit every logical block that you wrote.
Descriptive commit messages: When the commit messages are meaningful, concise and easy to read.


#### What’s the difference between git and GitHub?
Git is a version control system used for tracking changes in source code during software development.
Github is a website used for hosting git repositories in the cloud.


## Software design

### Clean code

#### What does clean code mean?
Your code is DRY. Easy to read, easy to understand, easy to maintain. No dead code, no repetition, no clutter.


#### What steps do we usually do during a clean code refactoring?
First we need to try and understand the code. Then we start with checking variable and function names, and replace them if needed. Then we eliminate global variables and magic numbers. In the end, the code should be free of clutter, complexity and cleverness.


### Error handling

#### What is exception handling?
Exception handling is the process of responding to the occurrence of exceptions often disrupting the normal flow of program execution. Instead of crashing, the program handles exceptions in a more graceful way.


#### What are the basics of exception handling in Python?
We use try-except blocks.
If the try block runs to failure, it jumps to the except block rather than crashing. The except block contains the logic that deals with the exception gracefully.


#### In which case should we catch an exception? Why?
We should catch only well defined, foreseeable exceptions to maintain flow control. Defining broader exceptions may cause the program to not work as expected.


#### What can/should we do with an exception in the ‘except’ block?
We should tell the program how to continue executing our code. E.g. to print an error message and jump back to the try block.


#### What does the else and finally statement do in a try-except block in Python?
The else block is executed when the except block doesn't catch an exception. The finally block is always executed.


## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
A retrospective should take place after a peer review and before the next sprint planning. It is an opportunity for the team (Scrum Team?) to inspect itself and create a plan (with action items) for improvements to be enacted during the next sprint.
What went well in the sprint?
What could be improved?
What will we commit to improve in the next sprint? Action items


## Programming environment

### Unix

#### What is UNIX and what is Linux?
UNIX is a family of multitasking multiuser computer operating systems from the 70's. It has a modular design and a command line interface.
Linux is a family of open source Unix-like operating systems based on the Linux kernel (first released in 1991 by Linus Torvalds).
Linux is free (open source), but UNIX is licensed. Unix-like systems are very similar to UNIX, even though they are not certified to be UNIX systems. Linux also has a GUI (Graphical User Interface).


#### What do we call the shell in Linux?
A shell provides a command line user interface for Unix-like operating systems. The shell is both an interactive command language and a scripting language, and is used by the operating system to control the execution of the system using shell scripts.
The shell is a program that takes operations from the user and gives it to the OS.
GNU BASH / Bash (Bourne Again Shell). It's not part of the kernel, but it uses it to run itself. It is also called simply the terminal.
Bash is a free Unix shell and command language. It is the default login shell for most Linux distros and macOS (up until Mojave).
Bash is a command processor that runs in a text window where the user types commands that cause actions. Bash can also read and execute commands from a file (shell script).


#### What does root means in a Linux environment?
An account that has access to all commands and files. It is usually referred to as the superuser. sudo -i
There's also a root directory, all of the directories and files are in there. cd /


#### How do you access your personal files in Linux?
Personal files are in the Home directory. cd ~


#### How can you install an application in Linux?
You can download and install it from the Ubuntu software (or equivalent), or download it using the terminal. sudo apt-get install application


#### What is package management in Linux, what are repositories?
Package management keeps track of the users' software packages. It tells the user whenever there's a new version of an installed software is available.
The repository is storage location where new softwares get installed and existing softwares get updated by the OS, also this is where the OS updates itself.


#### How do you navigate in the filesystem with the command line?
pwd: Print working directory.
ls: List items.
cd: Change directory.


#### What does the following commands do: mkdir, rm, cat, cp, touch?
mkdir: Create new folder (directory).
rm: Remove file or folder (directory).
cat: Concatenate files and print to standard output.
cp: Copy file or folder (directory).
touch: Create new file.


#### How can you look up what does a command do in Linux if you have no internet connection?
man command
command --help


#### What does the following commands do: head, tail, more, less?
head: Print the first 10 lines to standard output.
tail: Print the last 10 lines to standard output.
more: View one screenful of text at a time.
less: Similar to more, but faster, and you can navigate through the file. Better for large files.


#### How do you download a file from internet using the terminal?
wget URL
