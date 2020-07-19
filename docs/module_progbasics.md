# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!

The purpose of a list is to store values in a sequence. 
Lists are also useful data structures because they are iterable and mutable.

Methods:
1. **len():** *Returns the length of a list (number of items in the list) as an integer* **len(list)**
2. **append():** *Adds a single item to the end of the list.* **list.append(item)**
3. **insert():** *Inserts item to the list.*- **list.insert(index, item)**
4. **remove():** *Removes item from the list.* **list.remove(item)**
5. **count():** *Counts an item in a list, returns an integer* **list.count(item)**
6. **index():** *Returns smallest index of item in list.* **list.index(item)**

#### What is the difference between a list/array and a set?
Lists/arrays can contain the same element multiple times while in sets every element can occur only once. Sets are unordered and elements don't have indices while list elements are indexed. An empty list is declared as lst = [] while an empty set is declared as set = {}

#### What is the purpose and methods of a dictionary/map data structure?
Dictionaries can store a collection of key-value pairs. Dictionaries are unordered, mutable and indexed. dict = {key1: value1, key2: value2, }
They can be practical to store data by names or for taking inventory of items for example. 

Methods:
1. **dict():** *Creates a dictionary in Python.* **dict({key: value})**
2. **get():** *Returns value based on key or None if it doesn't exist.* **dict.get(key)**
3. **update():** * Much like append in lists. Adds several items to the dictionary once. Also can change already existing value.*
4. **keys()** *Returns the keys of the dictionary.* **dict.keys()**
5. **values()** *Returns the values of the dictionary.* **dict.values()**
6. **items()** *Returns both the keys and values of the dictionary.* **dict.items()**

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
Fn = F(n−1) + F(n−2)

```Python
def Fibonacci(n):
    if n<0:
        print("Incorrect input")
    elif n==1:
        return 0
    elif n==2:
        return 1
    else:
        return Fibonacci(n-1) + Fibonacci(n-2)
```
#### How do you find a max value in a list/array if you can’t use any built-in functions?
#### How do you find the average of values in a list/array if you can’t use any built-in functions?
#### What do we call an *in-place* sort?
#### Explain an algorithm which sorts a list!

### Programming paradigms - procedural

#### What is the call stack?
#### What is “Stack overflow”?
#### What are the main parts of a function?

### Programming languages - Python  
#### How do you use a dictionary in Python?
#### What does it mean that an object is immutable in Python?
#### What is conditional expression in Python?
#### What are different types of arguments in Python?
#### What is variable shadowing? (context: variable scope)
#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
#### If you need to access the iterator variable after a for loop, how would you do it in Python?
#### What type of elements can a list contain in Python?
#### What is slice operator in Python and how to use?
#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
#### What is the purpose of the in and not in membership operators in Python?
#### What does the + operator mean when used with strings in Python?
#### Explain f strings in Python?
#### Name 4 iterable types in Python!
#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
#### Does the order of the function definitions matter in Python? Why?
#### What does unpacking mean in Python?
#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
#### What does step over, step into and step out mean while using the debugger?
#### How can you start to debug a program from a certain line using the debugger?

### Version control

#### What are the advantages of using a version control system?
#### What is the difference between the working directory, the staging area and the repository in git?
#### What are remote repositories in git?
#### Why does a merge conflict occur?
#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
#### What does it mean atomic commits and descriptive commit messages?
#### What’s the difference between git and GitHub?

## Software design

### Clean code

#### What does clean code mean?
#### What steps do we usually do during a clean code refactoring?

### Error handling

#### What is exception handling?
#### What are the basics of exception handling in Python?
#### In which case should we catch an exception? Why?
#### What can/should we do with an exception in the ‘except’ block?
#### What does the else and finally statement do in a try-except block in Python?

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?

## Programming environment

### Unix

#### What is UNIX and what is Linux?
#### What do we call the shell in Linux?
#### What does root means in a Linux environment?
#### How do you access your personal files in Linux?
#### How can you install an application in Linux?
#### What is package management in Linux, what are repositories?
#### How do you navigate in the filesystem with the command line?
#### What does the following commands do: mkdir, rm, cat, cp, touch?
#### How can you look up what does a command do in Linux if you have no internet connection?
#### What does the following commands do: head, tail, more, less?
#### How do you download a file from internet using the terminal?
