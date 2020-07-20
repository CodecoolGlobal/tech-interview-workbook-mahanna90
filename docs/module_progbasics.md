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

Fibonacci number output (only the #n number in the list):
```Python
def Fibonacci(n):
    if n<0:
        print("Incorrect input")
    elif n == 1:
        return 0
    elif n == 2:
        return 1
    else:
        return Fibonacci(n-1) + Fibonacci(n-2)
```
Fibonacci number list output:
```Python
def Fibonacci(n):
    fibonacci_nums = [0, 1, ]
    if n == 0:
        fibonacci_nums = []
    elif n == 1:
        fibonacci_nums = [0, ]
    else:
        for i in range(2, n):
            fibonacci_nums.append(fibonacci_nums[i-1] + fibonacci_nums[i-2])
    return fibonacci_nums
```

#### How do you find a max value in a list/array if you can’t use any built-in functions?
Iterate through the list once with a for cycle and check for each element if it is higher than the highest before. 
If so, store the actual value in the max_value variable. In the end max_value will contain the max element.

```Python
def find_max():
    num_list = [10, 9, 76, 3, -8]
    max_value = -1000000
    for item in num_list:
        if item > max_value:
            max_value = item
    return max_value
```

#### How do you find the average of values in a list/array if you can’t use any built-in functions?
Iterate through the list/array once, while counting the number of elements by incrementing the count variable and adding each element's value to the sum_list variable.
After the iteration is finished, we can divide the sum_list by the count and the result is the average value.

```Python
def find_average():
    num_list = [10, 9, 76, 3, -8]
    count = 0
    sum_list = 0
    for item in num_list:
        count += 1
        sum_list = sum_list  + item
    avg = sum_list/count
    return avg
```
#### What do we call an *in-place* sort?
Sorting a list without assigning its sorted outcome to any other variable. This only modifies the order of the elements within the list, but does not create a new list.

#### Explain an algorithm which sorts a list!
Bubble sort: The algorithm iterates through the list the number of times of the list's length. Each time it checks adjacent elements and if the next element is lower, it swaps them. This way it sorts the list into ascending order. 

```Python
def bubble_sort():
    num_list = [10, 9, 76, 3, -8]
    for i in range(len(num_list)):
        for j in range(len(num_list) - i - 1):
            if num_list[j] > num_list[j+1]:
                temp = num_list[j]
                num_list[j] = num_list[j+1]
                num_list[j+1] = temp
    return num_list
```

### Programming paradigms - procedural

#### What is the call stack?
The call stack is a stack data structure that stores information about the active subroutines of a program. 
It keeps track of the point to which each active subroutine (or method call) should return control when it finishes executing.
Subroutines may be nested to any level (recursive as a special case), hence the stack structure.

#### What is “Stack overflow”?
Stack overflow is an error which occurs when a program attempts to use more space than is available on the call stack.

#### What are the main parts of a function?
```Python
def function_name(parameter1, parameter2): # function definition name and parameters
    multiply = parameter1 * parameter2 # function body describing the routine
    return multiply # return value

function_name(argument1, argument2) # calling the function with arguments
```

### Programming languages - Python  
#### How do you use a dictionary in Python?
Dictionaries contain key-value pairs, are unordered, mutable and indexed.

```Python
#declaring a dictionary
dictionary = {'a': 2, 'b': 3, 'c': 4} # key-value pairs
#printing the dictdictionary
print(dictionary)
#getting the value of a key and store it
x = dictionary.get('a')
# variable x becomes equal to 2
```

other methods:
1. **update():** * Much like append in lists. Adds several items to the dictionary once. Also can change already existing value.*
2. **keys()** *Returns the keys of the dictionary.* **dict.keys()**
3. **values()** *Returns the values of the dictionary.* **dict.values()**
4. **items()** *Returns both the keys and values of the dictionary.* **dict.items()**
5. *Dictionaries can be sorted as well by key and by value as well (key=lambda function is useful for this)*

#### What does it mean that an object is immutable in Python?
These are of in-built types like int, float, bool, string, unicode, tuple.
An immutable object can't be changed after it is created.

#### What is conditional expression in Python?
Ternary operators also known as conditional expressions are operators that evaluate something based on a condition being true or false. 
It simply allows to test a condition in a single line replacing the multiline if-else making the code compact.

```Python
a, b = 10, 20
# Copy value of a in min if a < b else copy b 
min = a if a < b else b 
```
or

```Python
# Python program to demonstrate nested ternary operator 
a, b = 10, 20
if a != b: 
    if a > b: 
        print("a is greater than b") 
    else: 
        print("b is greater than a") 
else: 
    print("Both a and b are equal") 
```

#### What are different types of arguments in Python?
1. **Default Arguments:** *def sum(a=4, b=2):*
2. **Keyword Arguments:** *def print_name(name1, name2): print_name(name2 = 'John', name1 = 'Gary')*
3. **Variable-length Arguments:** *def display(\*name, \*\*address): display('john','Mary','Nina',John='LA',Mary='NY',Nina='DC')*

#### What is variable shadowing? (context: variable scope)
In computer programming, variable shadowing occurs when a variable declared within a certain scope (decision block, method, or inner class) has the same name as a variable declared in an outer scope. At the level of identifiers (names, rather than variables), this is known as name masking.
This outer variable is said to be shadowed by the inner variable, while the inner identifier is said to mask the outer identifier. This can lead to confusion, as it may be unclear which variable subsequent uses of the shadowed variable name refer to.

#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
Usually **IndexError: list index out of range** would occur, but there are exceptions. 
For example the while loop below can be run without the error. 
```Python
i = 0
while i < len(lst):
    if lst[i] == 1:
        del lst[i]
    else:
        i += 1
```
Normally modifying the data structure makes the iteration invalid because the length and indices change. 
*Error may not occur in the following cases either:*
1. Deleting an item from the list: the for loop will skip some elements, because we changed the list(indexing).
2. Adding an item to the list: the for loop will run forever.

#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
Scope: the part of a program where a variable is accessible.
In Python the LEGB rule is used to decide the order in which the namespaces are to be searched for scope resolution.

*Four different scopes (LEGB): local, enclosing, global, and built-in (in hierarchical order)*
1. **Local:** Defined variable within a function, its scope lies only within the function. It is accessible from the point at which it is defined until the end of the function and exists for as long as the function is executing.
2. **Enclosing:** Defined inside enclosing functions(Nested functions' inner parts)
3. **Global:** Whenever a variable is defined outside any function, it becomes a global variable, and its scope is anywhere within the program. 
4. **Built-in:** All the special reserved keywords fall under this scope. We can call the keywords anywhere within our program without having to define them before use.

#### If you need to access the iterator variable after a for loop, how would you do it in Python?
You can assign it to another variable inside the foor loop and the new variable can be used afterwards outside the for loop.

#### What type of elements can a list contain in Python?
Each item in a python list can be of any data type.
For example: Boolean, string, float, integer, lists, dict, tuple

#### What is slice operator in Python and how to use?
A slicing can be done with the slice() function or with list slicing.
The slice() function returns a part (slice) of an object.
```Python
a[start:stop:step] # list slicing
a[slice(start, stop, step)] # slice function
```

#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
```Python
NumList1 = [10, 20, 30]
NumList2 = [5, 2, 3]
add_lists = []
add = []
sub = []
multi = []
div = []
mod = []
expo = []

add_lists = NumList1 + NumList2

for j in range(3):
    add.append( NumList1[j] + NumList2[j])
    sub.append( NumList1[j] - NumList2[j])
    multi.append( NumList1[j] * NumList2[j])
    div.append( NumList1[j] / NumList2[j])
    mod.append( NumList1[j] % NumList2[j])
    expo.append( NumList1[j] ** NumList2[j])

print("The List Items after Merging = ", add_lists)
print("The List Items after Addition =  ", add)
print("The List Items after Subtraction =  ", sub)
print("The List Items after Multiplication =  ", multi)
print("The List Items after Division =  ", div)
print("The List Items after Modulus =  ", mod)
print("The List Items after Exponent =  ", expo)

output:
The List Items after Merging =   [10, 20, 30, 5, 2, 3]
The List Items after Addition =   [15, 22, 33]
The List Items after Subtraction =   [5, 18, 27]
The List Items after Multiplication =   [50, 40, 90]
The List Items after Division =   [2.0, 10.0, 10.0]
The List Items after Modulus =   [0, 0, 0]
The List Items after Exponent =   [100000, 400, 27000]
```

#### What is the purpose of the in and not in membership operators in Python?
Membership operators are operators used to validate the membership of a value. It tests for membership in a sequence, such as strings, lists, or tuples.
1. in operator: The ‘in’ operator is used to check if a value exists in a sequence or not. Evaluates to true if it finds a variable in the specified sequence and false otherwise.
2. ‘not in’ operator: Evaluates to true if it does not find a variable in the specified sequence and false otherwise.

#### What does the + operator mean when used with strings in Python?
It concatenates the strings, for example: "spam" + "eggs" -> spameggs

#### Explain f strings in Python?
Also called “formatted string literals,” f-strings are string literals that have an f at the beginning and curly braces containing expressions that will be replaced with their values.

Example:
```Python
answer = 456
print(f"Your answer is "{answer}"")
```

#### Name 4 iterable types in Python!
1. list
2. string
3. tuple
4. dictionary

#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
1. *List Comprehension:*  It is an elegant and compressed way of defining and creating a list. List comprehension allows us to create a list using for loops in one line.
```python
  values = [ expression for value in collection <if condition> ]
```

```python
  a_dict = {key: value  for key, value in zip(list1, list2) if clause}
```

2. *Generator Expressions:* Similar to list comprehensions, but instead of creating a list and keeping the whole sequence in the memory, the generator generates the next element in demand and allows us to create a generator without the yield keyword.

```Python
genexpr = ('Hello' for i in range(3))
```

*List Comprehension vs Generator Expressions:* 
List comprehension returns a list [] Generator expression returns an object that can be iterated through ()
The generator yields one item at a time and generates item only when in demand.
In case of a list comprehension Python reserves memory for the whole list so we can say that generator expressions are more memory efficient than lists.

#### Does the order of the function definitions matter in Python? Why?
The order won't change the result of the program because the function calls matter, but it can help to understand the code more easily if it is ordered properly.

#### What does unpacking mean in Python?
Unpacking in Python refers to an operation that consists of assigning an iterable of values to a tuple (or list ) of variables in a single assignment statement. As a complement, the term packing can be used when we collect several values in a single variable using the iterable unpacking operator.

For example if we want to give a list as argument to a function we can unpack the list with the "*" operator to give arguments by elements.
*lists use "\*" for unpacking:* 
```Python
def fun(a,b,c,d):
    print(a,b,c,d)
my list=[1,2,3,4]
fun(*my_list)
```
*dictionaries use "\*\*" for unpacking:* 
```Python
def fun(a, b, c): 
    print(a, b, c) 
d = {'a':2, 'b':4, 'c':10} 
fun(**d) 
```

#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
If there is no return statement the value None will be assigned to the variable and its type will become NoneType.


## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
1. print
2. debugger
3. rubberduck

#### What does step over, step into and step out mean while using the debugger?
1. **step  over:**  to skip certain functions (meaning it doesn't show it step by step)
2. **step into:** it allows to walk through the program step by step, and checks the functions as well line by line
3. **step out:** to step out the specific function

#### How can you start to debug a program from a certain line using the debugger?
1. Create breakpoint on desired line (with red dot)
2. Run the debugger

### Version control

#### What are the advantages of using a version control system?
1. Collaboration
2. Storing versions (Properly)
3. Restoring previous versions
4. Understanding what happened (commits)
5. Backup

#### What is the difference between the working directory, the staging area and the repository in git?
working directory: the directory where you are working on your computer (which is checked by git if the repository is created)
staging area: where the added changes can be checked before they are commited (they can be still deleted from staging)
git repository: storage of commited changes, which can be restored or merged later if needed (can be pushed to github)

#### What are remote repositories in git?
The remote repository is an online storage of the git repositories. 
It can be used to share code with colleagues by git push/pull commands and to manage multiple branches and merges between the versions. 

#### Why does a merge conflict occur?
A conflict arises when two separate branches have made edits to the same line in a file, or when a file has been deleted in one branch but edited in the other.

#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
0. repository is created by cloning or init.
1. *mv* - move file to that repo or create file with *touch <filename>*
2. *git add <filename>* - add file to staging
3. *git commit -m "commit message"* - create a commit with an appropriate message and add it to the local repo
4. *git push* - push the changes/commits to the remote repository (github)

#### What does it mean atomic commits and descriptive commit messages?
Atomic commit means every commit pertains to one fix or feature.
Descriptive commit means the purpose of the commit is clear from commit messages and description.

#### What’s the difference between git and GitHub?
Git is a distributed **version control tool** that can manage a development project's source code history, while GitHub is a **cloud based platform** built around the Git tool.

## Software design

### Clean code

#### What does clean code mean?
Code is clean if it can be understood easily, understandability comes readability, changeability, extensibility and maintainability.
No duplications, no dead code, meaningful variable names, proper indentation, functional structure and no magic numbers.

#### What steps do we usually do during a clean code refactoring?
1. Fix bad naming
2. Fix badly formatted code
3. Clear repetitive code
4. Refactor long methods
5. Fix wrong comment usage
6. Delete dead code

### Error handling

#### What is exception handling?
Exceptions are used to handle possible errors occurring during the program execution. Exceptions can anticipate the error type (if it is given) and when the error occurs
it will execute the coded lines inside the exception instead of crashing the program. 

#### What are the basics of exception handling in Python?
The error handling is done through the use of exceptions that are caught in try
blocks and handled in except blocks. If an error is encountered, a try block
code execution is stopped and transferred down to the except block.
In addition to using an except block after the try block, you can also use the
finally block. The code in the finally block will be executed regardless of whether an exception
occurs.

```Python
age = input("What is your age? ")
try:
    age = int(age)
except ValueError:
    print("Invalid Input!")
```

#### In which case should we catch an exception? Why?
Any time a specific error can be expected it is wise to use exceptions.
For example: when user input is used and the input type is important, when we are looking for files which may not exist, 
when we need to translate objects but it is not clear if it can be done, etc.

#### What can/should we do with an exception in the ‘except’ block?
Print an understandable error message or quit the program, if needed.

#### What does the else and finally statement do in a try-except block in Python?
*else block:* Will be executed only if the code inside the try block doesn’t generate an exception.
*finally block:* Code is always executed, whether the program executed properly or it raised an exception.

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
The goal is to discuss among the team members how the work went during the last sprint, 
what was good, what was bad, and what steps each member can take to improve the personal and team work. (SMART objectives)


## Programming environment

### Unix

#### What is UNIX and what is Linux?
Both of them are operating systems, but UNIX was earlier, it is running in CLI(Command Line Interface, meaning there is "only a command line, no mouse or graphical elements)
Linux (based on unix, but open source) is one or more steps forward, it enables applications and the users to access the devices on the computer to perform some specific function.

Usage:
*Unix:* The UNIX can be used in internet servers, workstations, and PCs.
*Linux:* Everyone for home PC use as well. Linux OS can be installed on various types of devices like mobile, tablet computers.

#### What do we call the shell in Linux?
The shell is the *command interpreter* in an operating system such Linux, it is a program that executes other programs. It provides a computer user an interface to the Unix/GNU Linux system so that the user can run different commands or utilities/tools with some input data (then executed by the operating system).

#### What does root mean in a Linux environment?
"root" is the user name or account that by default has access to all commands and files on a Linux or other Unix-like operating system. 
Basically the Windows "System Administrator" equivalent for Linux.

#### How do you access your personal files in Linux?
"cd" or "cd ~"in terminal or use the visual folders to search files 

#### How can you install an application in Linux?
You can use the software center, or you can use Linux package managers' commands, to install an application in the terminal.
command: apt install \<name_of_application>, or sudo apt install \<name_of_application> for admin install

#### What is package management in Linux, what are repositories?
Package managers are collections of software tools that manage the applications users can install, update, or delete. 
The most well known ones are: DPKG, APT, RPM, YUM

#### How do you navigate in the filesystem with the command line?
1. **pwd:** find your “present working directory”
2. **ls:** list the files in your current directory
3. **cd:** change your current directory
    1. *To navigate into the root directory, use* **cd /**
    2. *To navigate to your home directory, use* **cd** *or* **cd ~**
    3. *To navigate up one directory level, use* **cd ..**
    4. *To navigate to the previous directory (or back),* use **cd -**
    5. *To navigate into a folder/directory, use* **cd /<directory_name>**

#### What does the following commands do: mkdir, rm, cat, cp, touch?
1. **mkdir:** Make directory
2. **rm:** Remove files and directories (-rf -deletes folders aswell)
3. **cat:** Concatenate files and print to stdout.
4. **cp:** Copy files
5. **touch:** Create a new file or update its timestamp.

#### How can you look up what does a command do in Linux if you have no internet connection?
<commandname> -help/--help or <commandname> -h
man <commandname>

#### What does the following commands do: head, tail, more, less?
1. **head:** displays the first *ten* lines of a file, unless otherwise stated.
2. **tail:** display the last part of the file
3. **more:** to view a text file one page at a time, press spacebar to go to the next page
4. **less:** is much the same as more command

#### How do you download a file from internet using the terminal?
with wget:
1. sudo apt-get install wget
2. wget [URL]
