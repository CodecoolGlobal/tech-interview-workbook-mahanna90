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
`SELECT title FROM boards WHERE id = %(board_id)s""", {'board_id': board_id})`

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
```
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
```
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
```
max = lst[0] 
for x in lst: 
    if x > max: 
        max = x 
return max
```
__Method 2__: sort the list into desc or asc order with a bubble sort function for example, and select the last/first elements.

#### 19. Explain the process of calculating the average value in an array of numbers!
Adding each element's value together and dividing it with the the total element count.
```
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
`lst_avg = sum(lst) / len(lst)`

### Procedural
#### 22. How the CASE condition works in SQL?


#### 23. How the switch-case condition works in JavaScript?
#### 24. How to achieve a switch-case-like structure in Python?
#### 25. Explain variable scoping in Python!
#### 26. What’s the difference between const and var in JavaScript?
#### 27. How the list comprehension looks like in Python?
#### 28. How the “ternary expression” looks like in Python?
#### 29. How the ternary expression looks like in JavaScript?
#### 30. How to import a function from another module in Python?
#### 31. How to import a function from another module in JavaScript?

### Functional
#### 32. What is recursion?
#### 33. Write a recursive function which calculates the Fibonacci numbers!
#### 34. How to store a function in a variable in Python?
#### 35. List the ways of defining a callable logical unit in JavaScript!
#### 36. What is an event listener? How to attach one?
#### 37. How to trigger an event in JavaScript?
#### 38. What is a callback function? Tell some examples of its usage.
#### 39. What is a Python decorator? How does it work? Tell some examples of its usage.
#### 40. What is the difference between synchronous and asynchronous execution?

## Programming languages

### SQL

#### 41. How can you connect your application to a database server? What are the possible ways?
#### 42. When do you use the DISTINCT keyword in SQL?
#### 43. Talk about the behavior/goal of these base SQL clauses: WHERE, GROUP BY, HAVING, ORDER BY?
#### 44. What are aggregate functions in SQL? Give 3 examples.
#### 45. What kind of JOIN types do you know in SQL? Could you give examples?
#### 46. What are the constraints in sql?
#### 47. What is a cursor in SQL? Why would you use one?
#### 48. What are database indexes? When to use?
#### 49. What are database transactions? When to use?
#### 50. What kind of database relations do you know? How to define them?
#### 51. You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
#### 52. How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?

### HTML & CSS

#### 53. What’s the difference between XML, XHTML and HTML?
#### 54. How to include a JavaScript file in a webpage?
#### 55. How to include a CSS file in a webpage?
#### 56. How to select an element using its id in CSS?
#### 57. How to select elements using their class in CSS?
#### 58. How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
#### 59. How to select all list items in all ordered lists on the page in CSS?
#### 60. How to select elements using their attributes in CSS?
#### 61. What are UX and UI?
#### 62. Please list some points that an application should fulfill to have good UX.
#### 63. What is XML, XSLT, DTD?
#### 64. What is the difference between HTML and XML?

### Javascript

#### 65. What is javascript?
#### 66. When to use AJAX? Bring examples of its usage.
#### 67. What is DOM and how to manipulate it from Javascript?
#### 68. What are events and how/why to use them in Javascript?
#### 69. What is event bubbling/capturing? How would you use it?
#### 70. What is JSON and how do we use it?

## Software engineering

### Version control

#### 71. What type of branching strategy would you use?
#### 72. What would you do if you find a bug on the production code (master branch)?
#### 73. How can you move changes from one branch to another in GIT?
#### 74. How does a VCS help with code reviews?
#### 75. What is your favorite git command? Why?
#### 76. What does remote/local mean in Git? 

### DevOps

#### 77. Why is it good to use a package manager software?
#### 78. Why is it good to use a virtual environment for a project?

### Networks

#### 79. What kind of HTTP status codes do you know?
#### 80. What is a API?
#### 81. What is REST API?
#### 82. What is JSON? When to use?
#### 83. What is TCP/IP? What layers does it define, what are they responsible for?
#### 84. What’s the difference between TCP and UDP?
#### 85. How does an HTTP Request look like? What are the most relevant HTTP header fields?
#### 86. How does an HTTP Response look like? What are the most relevant HTTP header fields?
#### 87. What is DNS? How does it work?
#### 88. What is a web server?
#### 89. Explain the client-server architecture.
#### 90. What would you use a session for?
#### 91. What would you use a cookie for?

## Software Development Methodologies

#### 92. What kind of software development methodologies do you know? What are the main features of these?
#### 93. What are the SCRUM roles?
#### 94. What are the SCRUM ceremonies?
#### 95. What are the SCRUM artifacts?
#### 96. What is the main goal of a retrospective meeting?
#### 97. Explain, when would you recommend to use the waterfall methodology?
