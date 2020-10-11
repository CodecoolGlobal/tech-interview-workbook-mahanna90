# Web with Python questions

## Software design

### Clean code

#### 1. Point out 5 suggestions, how to format an SQL query!
1. Descriptive nameing with related but different database and table names
2. Keywords and expressions are aligned into a column and start in new lines
3. Indented new line after every logical step (case for example)
4. Query parameters indented to create a block like body
5. Commas are at the end of the line

#### 2. What layers can you name in a simple web application?
- View layer (UI)<br>
- Application service (business logic layer)<br>
- Data layer (data access, database)<br>

### Error handling
#### 3. What error can occur, when an array does not have an element on the requested index?
IndexError

#### 4. What is the “finally” block, and how would you use it?
Finally block is used both in python and javascript to run important code. <br>
It can be used in conditional statements or with fetch in JS for example.<br>
The finally block is __always executed__ whether exception is handled or not.<br>
(example: Try-catch-finally, if-else-finally or fetch-then-catch-finally)<br>

#### 5. Why should we catch special exception types?
Exceptions can handle expected and unexpected errors during the progrum run, without crashing and stalling the program itself.<br>
They can handle problematic user interactions like bad (type/format etc) user input or index errors.<br>
Harmful injections can be handled with exceptions as well.<br>


### Security
#### 6. What is SQL injection? How to protect an application against it?
An SQL injection is a computer attack in which malicious code is inserted into a poorly-designed application and then passed to the backend database.<br>
You can prevent SQL Injection vulnerabilities in web applications by utilizing parameterized database queries with bound, typed parameters and careful use of parameterized stored procedures in the database.<br>
Example: <br>
```SQL
SELECT title FROM boards WHERE id = %(board_id)s""", {'board_id': board_id})
```

#### 7. What is XSS? How to protect an application against it?
Cross-site Scripting (XSS) is a client-side code injection attack.<br>
The attacker aims to execute malicious scripts in a web browser by including malicious code in a legitimate web page or web application. <br>
Commonly used for Cross-site Scripting attacks are forums, message boards, and web pages that allow comments.<br>
To protect against stored XSS attacks, make sure any dynamic content coming from the data store cannot be used to inject JavaScript on a page.<br>
Examples for protection: <br>
- Whitelist Values<br>
- HTTP-only Cookies : meaning that cookies will be received, stored, and sent by the browser, but cannot be modified or read by JavaScript.<br>
- Disallow the characters – especially `<` and `>` characters – from being rendered<br>

#### 8. How to properly store passwords?
You have to hash them(salting them is also recommended) and then store the outcome in a database.<br>
Example for hashing:<br>
```Python
def hash_password(plain_text_password):
    hashed_bytes = bcrypt.hashpw(plain_text_password.encode('utf-8'), bcrypt.gensalt())
    return hashed_bytes.decode('utf-8')

def verify_password(plain_text_password, hashed_password):
    hashed_bytes_password = hashed_password.encode('utf-8')
    return bcrypt.checkpw(plain_text_password.encode('utf-8'), hashed_bytes_password)
```

#### 9. What is HTTPS?
Hypertext Transfer Protocol Secure (HTTPS) is an extension of the Hypertext Transfer Protocol (HTTP). <br>
It is used for secure communication over a computer network, and is widely used on the Internet. It protects against man-in-the-middle attacks, uses encryption and validation.

#### 10. What is encryption and decryption?
Encryption is the process of encoding information. This process converts the original representation of the information, known as plaintext, into an alternative form known as ciphertext. Ideally, only authorized parties can decipher a ciphertext back to plaintext and access the original information. <br>
Decryption is conversion of encrypted data into its original form. It is generally a reverse process of encryption. It decodes the encrypted information so that an authorized user can only decrypt the data because decryption requires a secret key or password.

#### 11. What is hashing?
A hash function is where a computer takes an input of any length and content (e.g. letters, numbers, and symbols) and uses a mathematical formula to chop it, mix it up, and produce an output of a specific length. A hashed password cannot be restored to original, but there are algorithms which can guess the original value by comparing it to often used passwords (brute-force attack).
Example for hash function:
```Python
def hash_password(plain_text_password):
    hashed_bytes = bcrypt.hashpw(plain_text_password.encode('utf-8'), bcrypt.gensalt())
    return hashed_bytes.decode('utf-8')

def verify_password(plain_text_password, hashed_password):
    hashed_bytes_password = hashed_password.encode('utf-8')
    return bcrypt.checkpw(plain_text_password.encode('utf-8'), hashed_bytes_password)
```


#### 12. What is the difference between encryption and hashing? When would you use which?
The key difference between encryption and hashing is that encrypted strings can be reversed back into their original decrypted form if you have the right key. Therefore hashing is ideal for storing passwords, because they cannot be decrypted only guessed. Encryption is ideal for transmitting data and for making private data available to multiple privileged parties.

#### 13. What encryption methods do you know?
1. AES (Advanced Encryption Standard):
Advanced Encryption Standard is a symmetric encryption algorithm that encrypts fixed blocks of data (of 128 bits) at a time.
2. RSA (Rivest-Shamir-Adleman):<br>
Considered an asymmetric algorithm due to its use of a pair of keys. Asymmetric encryption uses two separate keys-one public (shared with everyone) and one private (known only to the key’s generator to decrypt data). 

#### 14. What hashing methods do you know?
1. MD5 (major weaknesses were uncovered)
2. SHA-2 (Secure Hash Algorithm)

#### 15. How/where would you store sensitive data (like db password, API key, ...) of your application?
Stored in db (or other source not accessable publicly) in hashed (or encrypted) form.

## Computer science

### Algorithms

#### 16. What is the difference between Stack and Queue data structure?
A __stack__ is a linear data structure in which elements can be inserted and deleted only from one side of the list, called the __top__.<br> 
A stack follows the __LIFO__ (Last In First Out) principle.<br> 
The insertion of an element into stack is called __push__ operation, and deletion of an element from the stack is called __pop__ operation.<br> 
In stack we always keep track of the last element present in the list with a pointer called __top__.<br>
A __queue__ is a linear data structure in which elements can be inserted only from one side of the list called __rear__, and the elements can be deleted only from the other side called the __front__.<br>
The queue data structure follows the __FIFO__ (First In First Out) principle, i.e. the element inserted at first in the list, is the first element to be removed from the list.<br>
The insertion of an element in a queue is called an __enqueue__ operation and the deletion of an element is called a __dequeue__ operation.<br>
In queue we always maintain two pointers, one pointing to the element which was inserted at the first and still present in the list with the front pointer and the second pointer pointing to the element inserted at the last with the rear pointer.

#### 17. What is BubbleSort? Describe the main logic of this sorting algorithm.
BubbleSort is a sorting method. Starting from the first element, comparing it with the next. If the next element higher then the previous move to the next. Else swap them. And so on till the last index. The algorithm iterates through the list the number of times of the list's length. Each time it checks adjacent elements and if the next element is lower, it swaps them. This way it sorts the list into ascending order. 
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

#### 18. Explain the process of finding the maximum and minimum value in a list of numbers!
__Method 1__: iterate through the list and compare each number to the previously highest or lowest (which is saved each time into a variable). If the current value is higher/lower than the previously saved max/min, the temporary value is changed to the current value.
```Python
max = lst[0] 
for x in lst: 
    if x > max: 
        max = x 
return max
```
__Method 2__: sort the list into desc or asc order with a bubble sort function for example, and select the last/first elements.

#### 19. Explain the process of calculating the average value in an array of numbers!
Adding each element's value together and dividing it with the the total element count.
```Javascript
const average = list => list.reduce((prev, curr) => prev + curr) / list.length;

const list = [0, 10, 20, 30]
average(list) // 15
```

#### 20. What is Big O complexity? Explain time and space complexity!
__Big O Notation__ is to describe the complexity of an algorithm: how long an algorithm takes to run. It is to compare the efficiency of different solutions.<br>
Big O notation characterizes functions according to their growth rates.<br>
We need to compare the performance of different algorithms and choose the best one to solve a particular problem. While analyzing an algorithm, we mostly consider time complexity and space complexity.
__Time complexity__ of an algorithm quantifies the amount of time taken by an algorithm to run as a function of the length of the input.<br>
Similarly, __Space complexity__ of an algorithm quantifies the amount of space or memory taken by an algorithm to run as a function of the length of the input.

#### 21. Explain the process of calculating the average value in a list of numbers!
Adding each element's value together and dividing it with the the total element count.
```Python
lst_avg = sum(lst) / len(lst)
```

### Procedural
#### 22. How the CASE condition works in SQL?
The __CASE__ statement goes through conditions and returns a value when the first condition is met (like an IF-THEN-ELSE statement). <br>
So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.<br>
If there is no ELSE part and no conditions are true, it returns NULL.<br>
Example: <br>
```SQL
SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```

#### 23. How the switch-case condition works in JavaScript?
The switch statement is used to perform different actions based on different conditions.<br>
Use the switch statement to select one of many code blocks to be executed.
Example: <br>
```Javascript
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```
*Note: If we omit the break statement, the next case will be executed even if the evaluation does not match the case.*

#### 24. How to achieve a switch-case-like structure in Python?
The Pythonic way to implement switch statement is to use the powerful dictionary mappings, also known as associative arrays, that provide simple one-to-one key-value mappings.<br>
```Python
def switch_demo(argument):
   switcher = {
       1: "January",
       2: "February",
       3: "March",
       4: "April",
       5: "May",
       6: "June",
       7: "July",
       8: "August",
       9: "September",
       10: "October",
       11: "November",
       12: "December"
   }
   print(switcher.get(argument, "Invalid month")) # Invalid month is default if number not found
```

#### 25. Explain variable scoping in Python!
Scope: the part of a program where a variable is accessible.<br>
In Python the __LEGB__ rule is used to decide the order in which the namespaces are to be searched for scope resolution.<br>

*Four different scopes (LEGB): local, enclosing, global, and built-in (in hierarchical order)*
1. **Local:** Defined variable within a function, its scope lies only within the function. It is accessible from the point at which it is defined until the end of the function and exists for as long as the function is executing.
2. **Enclosing:** Defined inside enclosing functions(Nested functions' inner parts)
3. **Global:** Whenever a variable is defined outside any function, it becomes a global variable, and its scope is anywhere within the program. 
4. **Built-in:** All the special reserved keywords fall under this scope. We can call the keywords anywhere within our program without having to define them before use.

#### 26. What’s the difference between const and var in JavaScript?
Before 2015, using the __var__ keyword was the only way to declare a JavaScript variable.<br>
The 2015 version of JavaScript (ES6 - ECMAScript 2015) allows the use of the __const__ keyword to define a variable that cannot be reassigned, <br>
and the __let__ keyword to define a variable with restricted scope.

#### 27. How the list comprehension looks like in Python?
*List Comprehension* is an elegant and compressed way of defining and creating a list. List comprehension allows us to create a list using for loops in one line.
```Python
  values = [ expression for value in collection <if condition> ]
```

```Python
  a_dict = {key: value  for key, value in zip(list1, list2) if clause}
```

#### 28. How the “ternary expression” looks like in Python?
Ternary expressions allow to test a condition in a single line replacing the multiline if-else making the code compact.<br>
`value_if_true if condition else value_if_false` 

```Python
a, b = 10, 20
# Copy value of a in min if a < b else copy b 
min = a if a < b else b 
```

#### 29. How the ternary expression looks like in JavaScript?
`condition ? exprIfTrue : exprIfFalse`

Example: <br>
```Javascript
var age = 26;
var beverage = (age >= 21) ? "Beer" : "Juice";
console.log(beverage); // "Beer"
```

#### 30. How to import a function from another module in Python?
```Python
from file_name import func_1, func_2
from Flask import render_template
```

#### 31. How to import a function from another module in JavaScript?
```Javascript
// in source file
export function myFunc{};

//in target file
import {myFunc} from "my-module.js";
import "my-module.js";
import {reallyReallyLongModuleMemberName as shortName} from "my-module.js";
```


### Functional
#### 32. What is recursion?
Recursion is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem.<br>
Such problems can generally be solved by iteration, but this needs to identify and index the smaller instances at programming time. <br>
Recursion solves such recursive problems by using functions that call themselves from within their own code. 
*Other uses: copying or deleting a folder in a recursive way will delete/copy the sub folders too.*

#### 33. Write a recursive function which calculates the Fibonacci numbers!
Python example:
```Python
def fibonacci(n):  
    # Taking 1st two fibonacci nubers as 0 and 1  
    FibArray = [0, 1]  
      
    while len(FibArray) < n + 1:  
        FibArray.append(0)  
      
    if n <= 1:  
        return n  
    else:  
        if FibArray[n - 1] == 0:  
            FibArray[n - 1] = fibonacci(n - 1)  
  
        if FibArray[n - 2] == 0:  
            FibArray[n - 2] = fibonacci(n - 2)  
              
    FibArray[n] = FibArray[n - 2] + FibArray[n - 1]  
    return FibArray[n]  
      
print(fibonacci(9))  
```

Javascript example:
```Javascript
// for nth number
function fibonacci(limit, a=0, b=1) {
    if (b >= limit) {
        return
    }
    let c = a + b;
    console.log(c);
    return fibonacci(limit, b, c)
}
fibo(30);

// for array
function fib(n) {
  if (n == 0) return [0]
  if (n == 1) return [0, 1]
  const arr = fib(n - 1)
  return [...arr, arr[n-1] + arr[n-2]]
}
console.log(fib(15))
```


#### 34. How to store a function in a variable in Python?
```Python
def Testing(self):
    pass
x = Test()
```
OR
```Python
def my_func():
    print("hello from function one")
my_variable = my_func
```

#### 35. List the ways of defining a callable logical unit in JavaScript!
A callable object is a data structure that behaves as both an object and a function.<br>
__Arrow function__:<br>
```Javascript
const foo = (arg1, arg2) => {
    // function content
};
```
__Function declaration__ (const + arrow function):
```Javascript
const foo = (arg1, arg2) => {
        // function content
    };
```
__Before ES6__:
```Javascript
var foo = function (arg1, arg2) {
        // function content
    };
```
__Function in object literal__:
```Javascript
var obj = {
        myMethod: function (arg1, arg2) {
            ...
        }
    };

let obj = {
        myMethod(arg1, arg2) {
            ...
        }
    };
```

#### 36. What is an event listener? How to attach one?
An event listener is a procedure or function in a computer program that waits for an event to occur. <br>
Examples of an event are the user clicking or moving the mouse, pressing a key on the keyboard, disk I/O, network activity, or an internal timer or interrupt. The listener is programmed to react to an input or signal by calling the event's handler.<br>
Example:<br>
```Javascript
document.getElementById("myBtn").addEventListener("click", myFunction);

function myFunction() {
  document.getElementById("demo").innerHTML = "Hello World";
}
```

#### 37. How to trigger an event in JavaScript?
Events can be triggered by:
- mouse click (click, context menu)
- keyboard actions (keyup, keydown, keypress)
- content load (DOMContentLoaded, onload)
- change (onchange for input fields for eample)

#### 38. What is a callback function? Tell some examples of its usage.
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action. <br>
Callbacks are often used to continue code execution after an asynchronous operation has completed — these are called asynchronous callbacks. A good example is the callback functions executed inside a __.then()__ block chained onto the end of a promise after that promise fulfills or rejects. This structure is used in many modern web APIs, such as __fetch()__.
Example: <br>
```Javascript
function doHomework(subject, callback) {
 alert(`Starting my ${subject} homework.`);
 callback();
}
function alertFinished(){
 alert('Finished my homework');
}
doHomework('math', alertFinished);
```

#### 39. What is a Python decorator? How does it work? Tell some examples of its usage.
Decorators dynamically alter the functionality of a function, method, or class without having to directly use subclasses or change the source code of the function being decorated.<br>
Decorators allow us to wrap another function in order to extend the behavior of wrapped function, without permanently modifying it.<br>
In Decorators, functions are taken as the argument into another function and then called inside the wrapper function.<br>
Example: <br>
```Python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_whee():
    print("Whee!")
```

#### 40. What is the difference between synchronous and asynchronous execution?
When you execute something synchronously, you wait for it to finish before moving on to another task. When you execute something asynchronously, you can move on to another task before it finishes. <br>
__Synchronous__ operations block instructions until the task is completed, while __asynchronous operations__ can execute without blocking other operations. <br>
Asynchronous operations are generally completed by firing an event or by calling a provided callback function.<br>
During synchronous execution the code is executed in a linear order.<br>
During asynchronous execution when the webAPI completes a time consuming process the result is added to the Callback Queue.
The Event Loop waits for the Callstack to complete the loaded work. Once the Event Loop notices the Callstack is clear it will add work to the Callstack from the Callback Queue.<br>
Examples for javascript asynch functions: setInterval, setTimeout, .fetch(), promises


## Programming languages

### SQL

#### 41. How can you connect your application to a database server? What are the possible ways?
We need a connection string and a connection object from the database provider to set a session with the database server. For phyton we can use the psycopg2 module api's to connect an application with psql database. To create a connection we need to set the environment variables like username, password, host and db name.

__Everything On One Server__:<br>
*The entire environment resides on a single server. For a typical web application, that would include the web server, application server, and database server.*

__Separate Database Server__:<br>
*The database management system (DBMS) can be separated from the rest of the environment to eliminate the resource contention between the application and the database, and to increase security.*

Example for Python db connection function: <br>
```Python
def get_connection_string():
    user_name = os.environ.get('PSQL_USER_NAME')
    password = os.environ.get('PSQL_PASSWORD')
    host = os.environ.get('PSQL_HOST')
    database_name = os.environ.get('PSQL_DB_NAME')

    env_variables_defined = user_name and password and host and database_name

    if env_variables_defined:
        return 'postgresql://{user_name}:{password}@{host}/{database_name}'.format(
            user_name=user_name,
            password=password,
            host=host,
            database_name=database_name
        )
    else:
        raise KeyError('Some necessary environment variable(s) are not defined')

def open_database():
    try:
        connection_string = get_connection_string()
        connection = psycopg2.connect(connection_string)
        connection.autocommit = True
    except psycopg2.DatabaseError as exception:
        print('Database connection problem')
        raise exception
    return connection
```

#### 42. When do you use the DISTINCT keyword in SQL?
DISTINCT clause is used in the SELECT statement to remove duplicate rows from a result set.
Example: <br>
```SQL
SELECT DISTINCT Country FROM Customers;
```

#### 43. Talk about the behavior/goal of these base SQL clauses: WHERE, GROUP BY, HAVING, ORDER BY?
- __WHERE__:<br>
    It's used to "filter" the data based on conditions. It is used to extract only those records that fulfill a specified condition.
- __GROUP BY__:<br>
    The GROUP BY statement groups rows that have the same values into summary rows, like "find the number of customers in each country".<br>
    It is often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to group the result-set by one or more columns.
- __HAVING__:<br>
    HAVING is the same as WHERE. The HAVING clause was added to SQL because the WHERE keyword could not be used with aggregate functions.
- __ORDER BY__:<br>
    The ORDER BY keyword is used to sort the result-set in ascending or descending order.

#### 44. What are aggregate functions in SQL? Give 3 examples.
1. **COUNT()**: Returns the number of rows that matches a specified criterion.
2. **MAX()**: Returns the highest value of the selected column.
3. **MIN()**: Returns the smallest value of the selected column.
4. **SUM()**: Returns the total sum of a numeric column.
5. **AVG()**: Returns the average value of a numeric column.

#### 45. What kind of JOIN types do you know in SQL? Could you give examples?
__Inner Join:__<br>
Returns records at the intersection of the two tables.
```SQL
select first_name, last_name, order_date, order_amount
from customers c
inner join orders o
on c.customer_id = o.customer_id
```

__Left Join:__<br>
A left join returns all records from table A and any matching records from table B.
```SQL
select first_name, last_name, order_date, order_amount
from customers c
left join orders o
on c.customer_id = o.customer_id
```

__Right Join:__<br>
Right join is a mirror version of the left join and allows to get a list of all orders, appended with customer information.

__Full Join:__<br>
For a list of all records from both tables, we can use a full join.

#### 46. What are the constraints in sql?
SQL constraints are used to specify rules for data in a table.<br>
__NOT NULL__ ensures that a column cannot have a NULL value<br>
__UNIQUE__ ensures that all values in a column are different<br>
__PRIMARY KEY__ is a combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table<br>
__FOREIGN KEY__ uniquely identifies a row/record in another table<br>
__DEFAULT__  sets a default value for a column when no value is specified<br>

#### 47. What is a cursor in SQL? Why would you use one?
A cursor is a temporary work area created in the system memory when a SQL statement is executed.<br> 
A cursor contains information on a select statement and the rows of data accessed by it.<br>
This temporary work area is used to store the data retrieved from the database, and manipulate this data. <br>
A cursor can hold more than one row, but can process only one row at a time. The set of rows the cursor holds is called the active set.<br>

#### 48. What are database indexes? When to use?
A database index is a data structure that improves the speed of data retrieval operations on a database table at the cost of additional writes and storage space to maintain the index data structure. Indexes are used to quickly locate data without having to search every row in a database table.

#### 49. What are database transactions? When to use?
A transaction is a unit of work that you want to treat as "a whole." It has to either happen in full or not at all.<br>
A transaction generally represents any change in a database. <br>
Main purposes:<br>
1. To provide reliable units of work that allow correct recovery from failures and keep a database consistent even in cases of system failure, when execution stops (completely or partially) and many operations upon a database remain uncompleted, with unclear status.<br>
2. To provide isolation between programs accessing a database concurrently. If this isolation is not provided, the programs' outcomes are possibly erroneous.<br>

*A classical example is transferring money from one bank account to another. To do that you have to first withdraw the amount from the source account, and then deposit it to the destination account. The operation has to succeed in full. If you stop halfway, the money will be lost, and that is Very Bad.*<br>
*In modern databases transactions also do some other things - like ensure that you can't access data that another person has written halfway. But the basic idea is the same - transactions are there to ensure, that no matter what happens, the data you work with will be in a sensible state. They guarantee that there will NOT be a situation where money is withdrawn from one account, but not deposited to another.*

#### 50. What kind of database relations do you know? How to define them?
1. __One-to-One:__<br>
A row in table A can have only one matching row in table B, and vice versa.

2. __One-to-Many (or Many-to-One):__<br>
This is the most common relationship type. In this type of relationship,<br>
a row in table A can have many matching rows in table B,<br>
but a row in table B can have only one matching row in table A.<br>
(Each customer can only be assigned one city. One city can be assigned to many customers.)

3. __Many-to-Many:__<br>
A many-to-many relationship could be thought of as two one-to-many relationships,<br>
linked by an intermediary table( “cross-reference table”).<br>
(So in order to create a many-to-many relationship between the Customers table and the Products table,
we created a "switch" table called Orders.)

#### 51. You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
```SQL
SELECT * FROM table
WHERE address LIKE '%Miskolc%';
```

#### 52. How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
I would create a person_log table and insert a row into person_log table whenever the table/s row/s get updated/deletes/added.


### HTML & CSS

#### 53. What’s the difference between XML, XHTML and HTML?
Both HTML and XML are markup languages, which represent text data in proper format using tags. However they are used for completely different purposes.

Similarities between HTML and XML:
1. *Both are languages of web.*
2. *Both are markup languages.*
3. *Both are originated from SGML. "Standardized General Markup Language".*
4. *Tags are basic building blocks of both HTML and XML documents.*

Differences between HTML and XML:
1. *HTML tags are predefined tags where as XML tags are user defined tags.*
2. *HTML tags are limited number of tags where as XML tags are extensible.*
3. *HTML tags are case insensitive where as XML tags are sensitive.*
4. *HTML tags are meant for displaying the data but not for describing the data where as XML tags are meant for describing the data.*
5. *XML mainly focuses on transfer of data while HTML is focused on presentation of the data.*
6. *XML is content driven‭‬‬‬‬‬‬‬‬‬‬‬‬‬‬‬ whereas HTML is format driven‭‬‬‬‬‬‬‬.*

XHTML:
1. *XHTML stands for EXtensible HyperText Markup Language*
2. *XHTML is almost identical to HTML*
3. *XHTML is stricter than HTML*
4. *XHTML is HTML defined as an XML application*

#### 54. How to include a JavaScript file in a webpage?
Using the script tag in html file:
```HTML
<script type="text/javascript" src="path-to-javascript-file.js"></script>
```
*Instead of providing the JS source file, it is possible to write JS code directly into the SCRIPT tag.*

#### 55. How to include a CSS file in a webpage?
Using the link tag in html file:
```HTML
<link rel="stylesheet" type="text/css" href="stylesheet.css"/>
```

#### 56. How to select an element using its id in CSS?
Using hashtag(#) + the element id name:
```CSS
#elementIdName {
    /*code;*/
}
```

#### 57. How to select elements using their class in CSS?
Using dot(.) + the element class name:
```CSS
.elementClassName {
    /*code;*/
}
```

#### 58. How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
Using both classes without separation:
```CSS
.alpha.beta{
    /*code;*/
}
```

#### 59. How to select all list items in all ordered lists on the page in CSS?
Using the ordered tag which is < ol >:
```CSS
ol {
 /*code;*/
}
```

#### 60. How to select elements using their attributes in CSS?
```CSS
/*We can reach differently*/

[data-value] {
  /* Attribute exists */
}

[data-value="foo"] {
  /* Attribute has this exact value */
}

[data-value*="foo"] {
  /* Attribute value contains this value somewhere in it */
}

[data-value~="foo"] {
  /* Attribute has this value in a space-separated list somewhere */
}

[data-value^="foo"] {
  /* Attribute value starts with this */
}

[data-value|="foo"] {
  /* Attribute value starts with this in a dash-separated list */
}

[data-value$="foo"] {
  /* Attribute value ends with this */
}
```

#### 61. What are UX and UI?
UX design refers to the term “user experience design”, while UI stands for “user interface design”. <br>

__UI:__<br>
The "UI" in UI design stands for “user interface”. The user interface is the graphical layout of an application. It consists of the buttons users click on, the text they read, the images, sliders, text entry fields, and all the rest of the items the user interacts with. This includes screen layout, transitions, interface animations and every single micro-interaction. Any sort of visual element, interaction, or animation must all be designed.

__UX:__<br>
In broad terms: UX Design encompasses any and all interactions between a potential or active customer and a company. <br>
A user’s experience of the app is determined by how they interact with it. User experience is determined by how easy or difficult it is to interact with the user interface elements that the UI designers have created.

#### 62. Please list some points that an application should fulfill to have good UX.
- Meet the users' needs
- Have a clear hierarchy
- Consistency
- Understand accessibility
- Usability
- Simplicity
- Function over aesthetics
- Leave room for user error (predict, then adapt)

#### 63. What is XML, XSLT, DTD?
*HTML is an application of SGML(Standard Generalized Markup Language).*

__XML__ is a simplified subset of SGML. It stands for eXtensible Markup Language.<br>

__DTD__ stands for Document Type Declaration. It is a set of instructions that states what tags are usable and what (re)action they create. Each browser has a DTD set in it's programming set by the browser companies. This is how some tags will work in only one type of browser or version. It has the tags stated in it's DTD. XML makes it possible to create unique tag sets by applying it's own DTD. This makes the DTD more compatable with more browsers.*<br>

__XSLT__ stands for eXtensible Stylesheet Language Transformation. It is a strong verions of CSS that formats the XML page for viewing.

#### 64. What is the difference between HTML and XML?
1. HTML tags are predefined tags where as XML tags are user defined tags.
2. HTML tags are limited number of tags where as XML tags are extensible.
3. HTML tags are case insensitive where as XML tags are sensitive.
4. HTML tags are meant for displaying the data but not for describing the data where as XML tags are meant for describing the data.
5. XML mainly focuses on transfer of data while HTML is focused on presentation of the data.
6. XML is content driven‭‬‬‬‬‬‬‬‬‬‬‬‬‬‬‬ whereas HTML is format driven‭‬‬‬‬‬‬‬.
7. XML is strict for closing tag while HTML is not strict.


### Javascript

#### 65. What is javascript?
JavaScript is a scripting or programming language that allows you to implement complex features on web pages. <br>
  - it can update and change both HTML and CSS
  - it can calculate, manipulate and validate data.

#### 66. When to use AJAX? Bring examples of its usage.
__AJAX__ stands for "Asynchronous Javascript and XML".<br> 
AJAX programming is used for exchanging data in the background without actually disturbing the user experience, and for rendering the access of data more efficiently and effectively.
__Purposes:__ <br>
    - Form validation
    - Refresh content without rendering the whole DOM again
    - Login Forms
    - Auto-Complete(during search)
    - Voting and Rating (forums)
    - Updating page with user content
    - Chat rooms and instant messaging
    - Lightboxes instead of pop-ups
    - Animations for better UX 
    - Infinite scroll

#### 67. What is DOM and how to manipulate it from Javascript?
__DOM:__ Document Object Model of a webpage. The HTML DOM model is constructed as a tree of Objects.<br>
  - Creating, removing or replacing an element
  - Modifying an element's text and/or HTML content
  - Getting an element content and working with it

```Javascript
/* Find an element in the DOM by id, class or tag name  */
let element = document.querySelector('selector')

/* Change the style of an element */
element.style.background = "black";
element.classList.add("black");

/*Select an element and add an event listener to it for user interaction*/
let btn = document.querySelector('button');
btn.addEventListener('click', foo);

/*Crearte new elements and add them to the DOM*/
let newBlock = document.createElement('p');
document.body.insertAdjacentHTML("beforeend", newBlock);

/* Change or set the attribute of the selected element */
let div = document.querySelector('div');
div.setAttribute('contentEditable', '')
```

#### 68. What are events and how/why to use them in Javascript?
Events are actions or occurrences that happen in the system you are programming, which the system tells you about so you can respond to them in some way if desired. For example, if the user selects a button on a webpage, you might want to respond to that action by displaying an information box. <br>
Events can be triggered/fired by several different methods: mouse clicks, content load, keyboard action, change, drag, hover etc.<br>
Each available event has an event handler, which is a block of code (usually a JavaScript function) that runs when the event fires. <br>
The addEventListener() method is the most preferred way to add an event listener to an element in the DOM <br>
The eventlistener then calls the event handler function when the event is fired/triggered.<br>
Example: <br>
```Javascript
let btn = document.querySelector('button');
btn.addEventListener('click',function(event) {
    // function content which is executed when the event is fired
  });
```

#### 69. What is event bubbling/capturing? How would you use it?
__Event bubbling:__ When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors. <br>
__Event capturing:__ Tthe event is first captured by the outermost element and propagated to the inner elements.

*Note: most events bubble.*

#### 70. What is JSON and how do we use it?
JSON is short for *JavaScript Object Notation*, and is a way to store information in an organized, easy-to-access manner. <br>
It is an open standard file format, and data interchange format (also language-indepentent), that uses human-readable text to store and transmit data objects consisting of attribute–value pairs and array data types (or any other serializable value). <br>
It is a very common data format, with a diverse range of applications, such as serving as a replacement for XML in AJAX systems.<br>

How to use it:<br>
Used with key-value pairs in an object-like format.<br>
Javascript usually handles json data in string format.<br>
```Javascript
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [],
  "spouse": null
}
```


## Software engineering

### Version control

#### 71. What type of branching strategy would you use?
__Gitflow Workflow:__
  - Code in master branch is deployable at all times
  - Working on new features on a branch with descriptive naming
  - Commit to that branch locally and regularly send your work to the same-named branch on the server (atomic commits)
  - Open a pull request when you feel your changes are ready to be merged
  - After the new feature is revised and approved, merge it into master
  - Once your changes are merged and pushed to the master, you can and should delete the branch

#### 72. What would you do if you find a bug on the production code (master branch)?
I would report it to the project manager. And he/she would tell us how/who should fix it.<br>
Alternatively, I would create a hotfix branch, locate and fix the bug, after testing merge it back to master.

#### 73. How can you move changes from one branch to another in GIT?
Make and checkout to a new branch will copy the actual state of the original branch where can be rollback or set back status. <br>
Rebase or merge bring changes from another branch into the current one.
```git
git branch checkout <branchname>
git merge <branchname>
```

#### 74. How does a VCS help with code reviews?
Modern version control systems are designed to help address problems that teams face when collaborating.<br>
Breaking down silos and embracing more perspectives and conversations can enable you and your team to deliver better software.<br>
VCSes are designed to help multiple people collaboratively edit files. This makes sharing between multiple computers particularly easy. <br>
With using pull requests the changes are highlighted (conflicts as well) and they can be commented, approved before merging into the main branch.<br>
With proper roles, it is regulated who can change what in the codebase.<br>
Restoring previous version or lost data is also easier.

#### 75. What is your favorite git command? Why?
`git log` - I can see the history of changes<br>
`git push` - Usually means a bigger feature or a whole project was finished

#### 76. What does remote/local mean in Git? 
__remote__: Repository's server, online storage (GitHub).<br>
__local__ - The repository's offline, local, on-disk stored version, which we make the changes on.


### DevOps

#### 77. Why is it good to use a package manager software?
- They prevent mixing incompatible files/libraries.
- They establish a shared convention for managing libraries.(When new developers come onto your project, team, company, etc., they're likely to know the conventions of the package manager.
- They give you a standard way of versioning and distributing your own dependencies and files that don't belong in your repository.
- Some package managers provide additional features during installation.
- They tend to centralize hosting and distribution.
- Helps with complex dependency trees (and that can be managed downloading a dependency together with all its dependencies).
- Packages contain metadata, such as the software's name, description of its purpose, version number, vendor, checksum, and a list of dependencies necessary for the software to run properly

#### 78. Why is it good to use a virtual environment for a project?
- Dependency Management: Prevent conflicts between dependencies of multiple projects.
- Every project can have a single unique virtual environment with the specific packages.
- Your main package directory does not get FLOODED with unnecessary packages


### Networks

#### 79. What kind of HTTP status codes do you know?
- 200 OK
- 301 Moved Permanently
- 302 Found
- 400 Bad Request
- 403 Forbidden
- 404 Not Found
- 405 Method Not Allowed
- 408 Request Timeout
- 418 I'm a teapot
- 500 Internal Server Error
- 504 Gateway Timeout

#### 80. What is an API?
API stands for Application Programming Interface.<br>
An API is essentially a way for apps to borrow functionality and data from each other.<br>
An API is code, that allows two applications to communicate with each other. One program can call another programs API to get access to data or functionality of the other program.<br>
An API is the messenger that takes a request, tells a system what you want to do and then returns the response back to you.<br>
Modern APIs adhere to standards (typically HTTP and REST), that are developer-friendly, easily accessible and understood broadly

#### 81. What is REST API?
Short for Representational state transfer.<br>
Web services that conform to the REST architectural style, called RESTful Web services, provide interoperability between computer systems on the internet.<br>
Modern APIs adhere to standards (typically HTTP and REST), that are developer-friendly, easily accessible and understood broadly.<br>
A REST API is an application program interface (API) that uses HTTP requests to GET, PUT, POST and DELETE data.<br>
Six guiding constraints define a RESTful system: <br>
- Client-server architecture, 
- Statelessness, 
- Cacheability, 
- Layered system, 
- Code on demand (optional), 
- Uniform interface


#### 82. What is JSON? When to use?
JSON is short for *JavaScript Object Notation*, and is a way to store information in an organized, easy-to-access manner. <br>
It is an open standard file format, and data interchange format (also language-indepentent), that uses human-readable text to store and transmit data objects consisting of attribute–value pairs and array data types (or any other serializable value). <br>
It is a very common data format, with a diverse range of applications, such as serving as a replacement for XML in AJAX systems.<br>
Usage examples:
- sending data between back-end and fron-end
- storing data in the browser's storage
- sending/receiving data from webAPIs


#### 83. What is TCP/IP? What layers does it define, what are they responsible for?
__Transmission Control Protocol/Internet Protocol (TCP/IP)__ is the language a computer uses to access the internet.<br>
TCP provides reliable, ordered, and error-checked delivery of a stream of octets (bytes) between applications running on hosts communicating via an IP network. <br>
Major internet applications such as the World Wide Web, email, remote administration, and file transfer rely on TCP, which is part of the Transport Layer of the TCP/IP suite.<br>
It consists of a suite of protocols designed to establish a network of networks to provide a host with access to the internet.<br>
*(a set of rules to allow communication to each other)* <br>
TCP is connection-oriented, and a connection between client and server is established before data can be sent.

Layers:
- __Application Layer:__ Application layer interacts with an application program, which is closest to the end-user. Example of the application layer is an application such as file transfer, email, remote login, etc. (protocols: HTTP, SMTP, POP, Ping, FTP)<br>
- __Transport Layer:__ Transport layer builds on the network layer in order to provide data transport from a process on a source system machine to a process on a destination system. (protocols: TCP (reliable), UDP (not reliable))<br>
- __Internet Layer:__ An internet layer is a second layer of the TCP/IP model. It is also known as a network layer. The main work of this layer is to send the packets from any network, and any computer still they reach the destination irrespective of the route they take. (protocols: IP)<br>
- __Network Interface:__ Also called a network access layer. It helps to define details of how data should be sent using the network. (protocols: Ethernet, ATM, PPP)

#### 84. What’s the difference between TCP and UDP?
TCP (Transmission Control Protocol) is connection oriented, whereas UDP (User Datagram Protocol) is connection-less.<br>
This means that TCP tracks all data sent, requiring acknowledgment for each octet (generally). UDP does not use acknowledgments at all, and is usually used for protocols where a few lost datagrams do not matter.

#### 85. How does an HTTP Request look like? What are the most relevant HTTP header fields?
A simple request message from a client computer consists of the following components:<br>
  - A request line to get a required resource, for example a request GET /content/page1.html is requesting a resource called /content/page1.html from the server.
  - Headers (Example – Accept-Language: EN, others: General|Request|Entity|Authorization).
  - An empty line.
  - A message body which is optional.

*All the lines should end with a carriage return and line feed. The empty line should only contains carriage return and line feed without any spaces.* <br>
*Most used methods: GET, POST, PUT, DELETE.*

#### 86. How does an HTTP Response look like? What are the most relevant HTTP header fields?
A simple response from the server contains the following components:
  - HTTP Status Code (For example HTTP/1.1 301 Moved Permanently, means the requested resource was permanently moved and redirecting to some other resource).
  - Headers (Example – Content-Type: text/html; charset=utf-8 others: Connection|200 OK|Date|Server|Set-Cookie)
  - An empty line.
  - A message body which is optional.

#### 87. What is DNS? How does it work?
Domain Name System (DNS) is the Internet's equivalent of a phone book. It maintains a directory of domain names and translates them to Internet Protocol (IP) addresses.

#### 88. What is a web server?
__Hardver side:__ On the hardware side, a web server is a computer that stores web server software and a website's component files. (for example, HTML documents, images, CSS stylesheets, and JavaScript files) A web server connects to the Internet and supports physical data interchange with other devices connected to the web.<br>
__Software side:__ On the software side, a web server includes several parts that control how web users access hosted files. At a minimum, this is an HTTP server. An HTTP server is software that understands URLs (web addresses) and HTTP (the protocol your browser uses to view webpages). An HTTP server can be accessed through the domain names of the websites it stores, and it delivers the content of these hosted websites to the end user's device.<br>

*At the most basic level, whenever a browser needs a file that is hosted on a web server, the browser requests the file via HTTP. When the request reaches the correct (hardware) web server, the (software) HTTP server accepts the request, finds the requested document, and sends it back to the browser, also through HTTP. (If the server doesn't find the requested document, it returns a 404 response instead.)*

*Note: can be static or dynamic.*

#### 89. Explain the client-server architecture.
Client–server model is a distributed application structure that partitions tasks or workloads between the providers of a resource or service, called servers, and service requesters, called clients.<br>
It is an architecture of a computer network in which many clients (remote processors) request and receive service from a centralized server (host computer).<br>
Client computers provide an interface to allow a computer user to request services of the server and to display the results the server returns.

#### 90. What would you use a session for?
*A session is a group of user interactions with your website that take place within a given time frame. For example a single session can contain multiple page views, events, social interactions, and ecommerce transactions.* <br>

The purpose for __session__ is to store data that you (as the web application developer) would like to have preserved across page loads.<br>
Thus, you can set flags in your login script such as *logged_in* to check if the user is logged in, and on any other page check `session['logged_in'] == true`, instead of querying for that information.
  - Sessions use a cookie as a key of sorts, to associate with the data that is stored on the server side.
  - Session variables will be expired when users close the browser, or after a set period of time.

#### 91. What would you use a cookie for?
A cookie is a small piece of data stored on the user's computer by the web browser while browsing a website.<br>
You can save settings to cookie for the websites between visits, so its gonna remember your previous preferences.<br>
Authentication cookies are the most common method used by web servers to know whether the user is logged in or not. <br>
Not very safe, since hackers can reach and get your information.<br>
Expiration can be set.


## Software Development Methodologies

#### 92. What kind of software development methodologies do you know? What are the main features of these?
1. __Waterfall development methodology:__<br>
`-> Requirements -> Desing -> Implementation -> Verification -> Maintanance`<br> 
It’s a rigid linear model that consists of sequential phases (see above) in which distinct goals are accomplished.<br>
Each phase must be completed before the next phase can start, and traditionally there is no process for going back to modify the project or direction.

2. __Agile:__<br>
It is an adaptive approach which is able to respond to the changing requirements of the clients. Direct communication and feedback from customer.
    __Mmethodology:__<br>
    - Requirement/Features/User stories/Product Backlog
    - Scrum Team(with lead)
    - Sprint Planning(relative time)
    - Sprints 1-4 Weeks Duration
    - Production deployment
    - Done Checklist
    - Sprint Retrospective
    - Product review(customer input)
    - Potential Product Increment

#### 93. What are the SCRUM roles?
1. __Product Owner:__ serves as an interface between the team and other involved parties (stakeholders).
2. __Scrum Master:__ does not interfere in the decisions of the team regarding specifically the development, but rather is there for the team as an advisor. Helps to remove impediments, protects the Team from outside interference, and helps the Team to adopt Agile development practices.
3. __Development Team:__ it is a collection of individuals working together to develop and deliver the requested and committed product increments. It comprises of cross-functional members who are capable of achieving the sprint goals.

#### 94. What are the SCRUM ceremonies?
- Sprint Backlog Refinement
- Sprint Planning Meeting
- Daily Stand-up Meeting
- Sprint Review Meeting
- Sprint Retrospective Meeting

#### 95. What are the SCRUM artifacts?
Scrum Artifacts provide key information that the Scrum Team and the stakeholders need to be aware of for understanding the product under development, the activities being planned, and the activities done in the project. <br>

Most common:<br>
- Product Vision
- Sprint Goal
- Product Backlog
- Sprint Backlog
- Definition of Done
- Burn-Down Chart
- Increment

#### 96. What is the main goal of a retrospective meeting?
To reflect on their previous Sprint and to figure out how to improve as a team by asking – what went well, what did not and what can be improved. It allows the team to focus on its overall performance and identify strategies for continuous improvement.<br>
Usually __S.M.A.R.T goals__ are expected: Specific (simple, sensible, significant), Measurable (meaningful, motivating), Achievable (agreed, attainable)<br>
Relevant (reasonable, realistic and resourced, results-based), Time bound (time-based, time limited, time/cost limited, timely, time-sensitive).

#### 97. Explain, when would you recommend to use the waterfall methodology?
Use Waterfall when:
- Requirements are clear and fixed that may not change.
- There are no ambiguous requirements (no confusion).
- The project is short and cast is low.
- It is good to use this model when the technology is well understood.
- It is all you know and you have no support for change,
- Risk is zero or minimum.
- You focus your performance measures on delivery date and budget.
