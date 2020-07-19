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
    elif n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return Fibonacci(n-1) + Fibonacci(n-2)
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

*An alternative solution could be done by using the sort() method and getting the last element of the sorted list.*

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
Stack owerflow is an error which occurs when a program attempts to use more space than is available on the call stack.

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
5. *Dictionaries can be sorted as well by key and by value as well (key=Lambda function is useful for this)*

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

print("\The List Items after Merging = ", add_lists)
print("\nThe List Items after Addition =  ", add)
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
