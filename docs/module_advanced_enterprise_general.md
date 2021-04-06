# General enterprise questions

## Software engineering

### Architectures

#### 1. What is n-tier (or multi-tier) architecture?

In multi-tier architecture software is engineered to have processing, data management and presentation functions physically and logically separated for creating flexible and reusable applications.
This means that the different functions are hosted on several machines or clusters.
A three-tier architecture is separated in the following tiers:

1. Logic tier
2. Presentation tier
3. Data tier

#### 2. What are microservices? Advantages and disadvantages?

Microservices are a way of breaking large software projects into loosely coupled modules, which communicate with each other through simple Application Programming Interfaces (APIs).
Advantages of microservice:

1. Smaller and faster developments, distributed development
2. Scalability
3. Ease of understanding
4. Improved fault isolation
5. Eliminate vendor or technology lock-in
6. Modularity
7. Integration of heterogeneous and legacy systems

Disadvantages of microservices:

1. Communication between services is complex
2. More services equal more resources
3. Global testing difficulty
4. Debugging problems can be harder
5. Deployment is more difficult

#### 3. What is Separation of Concerns?

Separation of concerns is a software architecture principle for separating an application in distinct sections, so each section addresses a separate concern. The overall goal of SoC is to establish a well-organized system where each part fulfils a meaningful and intuitive role while maximizing its ability to adapt to change.

#### 4. What is a layered design and why is it important in enterprise applications?

Layered architecture are n-tiered patterns where the components are organized in horizontal layers. This is the traditional method for designing most software and is meant to be self-independent. All components are interconnected but not dependent on each other.
Layered architecture has 4 layers

1. Presentation layer – contains all categories related to the presentation layer
2. Business layer – business logic
3. Persistence layer – used for function like object-relational mapping
4. Database layer – where all data is stored

Using a layered design for an enterprise application has a series of benefits, such as easy to test as components because are separated on different layers and easy to implement.

#### 5. What is Dependency Injection?

Dependency Injection (DI) is a design pattern used to implement IoC (inversion of control). It allows the creation of dependent objects outside of a class and provides those objects to a class through different ways. Using DI, we move the creation and binding of the dependent objects outside of the class that depends on them.

The Dependency Injection pattern involves 3 types of classes.

1. Client Class: The client class (dependent class) is a class which depends on the service class
2. Service Class: The service class (dependency) is a class that provides service to the client class.
3. Injector Class: The injector class injects the service class object into the client class.

#### 6. What is the DAO pattern? When and how to implement?

The Data Access Object (DAO) pattern is a structural pattern that allows us to isolate the application/business layer from the persistence layer (usually a relational database, but it could be any other persistence mechanism) using an abstract API.

The functionality of this API is to hide from the application all the complexities involved in performing CRUD operations in the underlying storage mechanism. This permits both layers to evolve separately without knowing anything about each other.

#### 7. What is SOA? When to use?

Service-Oriented Architecture (SOA) is a style of software design where services are provided to the other components by application components, through a communication protocol over a network.

The primary motivator for companies to switch to an SOA is the ability to reuse code for different applications. By reusing code that already exists within a service, enterprises can significantly reduce the time that is spent during the development process.

### Testing

#### 8. What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

**Unit testing** is a level of software testing where individual units/components of a software are tested. The purpose is to validate that each unit of the software performs as designed. A unit is the smallest testable part of any software.

**Integration testing** is a level of software testing where individual units are combined and tested as a group. The purpose of this level of testing is to expose faults in the interaction between integrated units. Test drivers and test stubs are used to assist in Integration Testing.

**Regression testing** is a type of software testing that intends to ensure that changes (enhancements or defect fixes) to the software have not adversely affected it.
The likelhood of any code changes impacting functionalities that are not directly associated with the code is always there and it is essential that regression testing is conducted to make sure that fixing one thing has not broken another thing.

**Acceptance testing** is a level of software testing where a system is tested for acceptability. The purpose of this test is to evaluate the system’s compliance with the business requirements and assess whether it is acceptable for delivery.

**System testing** is a level of software testing where a complete and integrated software is tested. The purpose of this test is to evaluate the system’s compliance with the specified requirements.

#### 9. What is code coverage? Why is it used? How you can measure?

Code coverage is the percentage of code which is covered by automated tests. Code coverage measurement simply determines which statements in a body of code have been executed through a test run, and which statements have not. In general, a code coverage system collects information about the running program and then combines that with source information to generate a report on the test suite's code coverage.

To calculate the code coverage percentage, simply use the following formula:

Code Coverage Percentage = (Number of lines of code executed by a testing algorithm/Total number of lines of code in a system component) \* 100.

#### 10. What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

Mocking is a process used in unit testing when the unit being tested has external dependencies. The purpose of mocking is to isolate and focus on the code being tested and not on the behavior or state of external dependencies. In mocking, the dependencies are replaced by closely controlled replacements objects that simulate the behavior of the real ones. There are 3 main possible types of replacement objects

1.  Fakes
2.  Stubs
3.  Mocks

**Fake** objects actually have working implementations, but usually take some shortcut which makes them not suitable for production.

**Stubs** provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test. Stubs may also record information about calls, such as an email gateway stub that remembers the messages it 'sent', or maybe only how many messages it 'sent'.

**Mocks** objects pre-programmed with expectations which form a specification of the calls they are expected to receive.

#### 11. What is a test case? What is an assertion? Give examples!

A **test case** is a set of actions executed to verify a feature or functionality of your software application. A test case contains test steps, test data, precondition, postcondition developed for specific test scenario to verify any requirement.

An **assertion** is a bool expression at a specific point in a program which will be true unless there is a bug in the program. A test assertion is defined as an expression, which encapsulates some testable logic specified about a target under test.

#### 12. What is TDD? What are the benefits?

The TDD (Test-driven development) methodology implies writing the unit test before writing the actual code. This process forces the developer to refactor and think about the unit’s interface and expected result. Whether or not the code is written correctly is apparent immediately when using this methodology.

TDD advantages:

1.  Better program design and higher code quality
2.  Detailed project documentation
3.  Reduces the time required for project development
4.  Code flexibility and easier maintenance
5.  Save project costs in the long run

#### 13. What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

1. Good test name
2. Arrange your test in Arrange, Act and Assert
3. Write minimal passing tests
4. Avoid magic strings
5. Avoid logic in tests
6. Avoid multiple asserts (only one assert per test)
7. Test public interfaces
8. Verify one use case per test

#### 14. What is arrange/act/assert pattern?

1.  **Arrange** – setup the testing objects and prepare the prerequisites for your test.
2.  **Act** – perform the actual work of the test.
3.  **Assert** – verify the result.

### DevOps

#### 15. What is continuous integration? Why is CI important?

Continuous integration (CI) is the practice of automating the integration of code changes from multiple contributors into a single software project. The CI process is comprised of automatic tools that assert the new code’s correctness before integration

CI is an asset to a software producing organization. CI benefits are not limited to the engineering team but greatly benefit the overall organization. CI enables better transparency and insight into the process of software development and delivery. These benefits enable the rest of the organization to better plan and execute go to market strategies.

#### 16. Why are tests important in the CI workflow?

If you test and deploy code more frequently, it will eventually reduce the risk level of the project you are working on as you can detect bugs and code defects earlier. This means they are easier to fix and you can fix them sooner which makes it cheaper to fix them.

#### 17. Name some software that help the CI workflow!

1. Jenkins
2. Travis
3. Circle CI
4. Gitlab CI

#### 18. What is Continuous Delivery?

Continuous Delivery is the ability to get changes of all types—including new features, configuration changes, bug fixes and experiments—into production, or into the hands of users, safely and quickly in a sustainable way.

#### 19. What is Continuous Deployment?

Continuous Deployment (CD) is a software release process that uses automated testing to validate if changes to a codebase are correct and stable for immediate autonomous deployment to a production environment.

#### 20. What is DevOps?

DevOps is a set of practices that works to automate and integrate the processes between software development and IT teams, so they can build, test, and release software faster and more reliably. The term DevOps was formed by combining the words “development” and “operations” and signifies a cultural shift that bridges the gap between development and operation teams, which historically functioned in siloes.

### Software Methodologies

#### 21. What kind of software-lifecycle models do you know?

1. Agile development
2. V-shaped model
3. Iterative approach
4. Spiral model
5. Waterfall model
6. Big Bang model

#### 22. What is a UML diagram? What kind of diagram types do you know?

A UML diagram is a diagram based on the UML (Unified Modeling Language) with the purpose of visually representing a system along with its main actors, roles, actions, artifacts or classes, in order to better understand, alter, maintain, or document information about the system.

Diagram types:

1. Class diagram
2. Package diagram

#### 23. What is a UML class diagram? What are the typical elements?

The UML Class diagram is a graphical notation used to construct and visualize object oriented systems. A class diagram in the Unified Modeling Language (UML) is a type of static structure diagram that describes the structure of a system by showing the system's:

1. Classes,
2. Their attributes,
3. Operations (or methods),
4. And the relationships among objects.

#### 24. What kind of design patterns do you know? Bring at least 3 examples.

1. Singleton pattern
2. Abstract Factory
3. Factory method
4. DAO

#### 25. What is the purpose of the Iterator Pattern?

Iterator is a behavioral design pattern that allows sequential traversal through a complex data structure without exposing its internal details.

#### 26. What do you know about the SOLID principles?

S.O.L.I.D is an acronym that represents five principles of object-oriented programming.

[S]ingle Responsibility Principle
[O]pen/Closed Principle
[L]iskov Substitution Principle
[I]nterface Segregation Principle
[D]ependency Inversion Principle

#### 27. How would you separate data storage code and business logic code (which uses stored data) in an application?

Using DAO pattern.

## Computer science

### Data Structures

#### 28. What is the difference between Stack and Queue data structure?

Stack: A stack is a linear data structure in which elements can be inserted and deleted only from one side of the list, called the top. A stack follows the LIFO (Last In First Out) principle, i.e., the element inserted at the last is the first element to come out.

Queue: A queue is a linear data structure in which elements can be inserted only from one side of the list called rear, and the elements can be deleted only from the other side called the front. The queue data structure follows the FIFO (First In First Out) principle, i.e. the element inserted at first in the list, is the first element to be removed from the list

#### 29. What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?

Graphs are a powerful and versatile data structure that easily allow you to represent real life relationships between different types of data (nodes). There are two main parts of a graph:

- The vertices (nodes) where the data is stored
- The edges (connections) which connect the nodes
  A graph with no loops and no parallel edges is called a simple graph.

A directed graph is graph, i.e., a set of objects (called vertices or nodes) that are connected together, where all the edges are directed from one vertex to another. A directed graph is sometimes called a digraph or a directed network. In contrast, a graph where the edges are bidirectional is called an undirected graph.

A weighted graph is a graph in which each branch is given a numerical weight. A weighted graph is therefore a special type of labeled graph in which the labels are numbers (which are usually taken to be positive).

#### 30. What are trees? What are binary trees? What are binary search trees?

A tree represents the nodes connected by edges.

Binary Tree is a special data structure used for data storage purposes. A binary tree has a special condition that each node can have a maximum of two children. A binary tree has the benefits of both an ordered array and a linked list as search is as quick as in a sorted array and insertion or deletion operation are as fast as in linked list.

Binary Search Tree is a node-based binary tree data structure which has the following properties:

- The left subtree of a node contains only nodes with keys lesser than the node’s key.
- The right subtree of a node contains only nodes with keys greater than the node’s key.
- The left and right subtree each must also be a binary search tree.

#### 31. How can you store graphs in programs? What are the advantages/disadvantages per each?

You can store a graph using:

- Nodes as objects with pointers to one another
- A matrix of edge weights

Nodes as objects with pointers to one another

- The memory complexity for this approach is O(n) because you have as many objects as you have nodes. The number of pointers (to nodes) required is up to O(n^2) as each node object may contain pointers for up to n nodes.
- The time complexity for this data structure is O(n) for accessing any given node.

Storing a matrix of edge weights

- This would be a memory complexity of O(n^2) for the matrix.
- The advantage with this data structure is that the time complexity to access any given node is O(1).

#### 32. What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?

Graph traversal algorithms are used to visit nodes in graph.

The Breadth First Search (BFS) traversal is an algorithm, which is used to visit all of the nodes of a given graph. In this traversal algorithm one node is selected and then all of the adjacent nodes are visited one by one. After completing all of the adjacent vertices, it moves further to check another vertices and checks its adjacent vertices again.

The Depth First Search (DFS) is a graph traversal algorithm. In this algorithm one starting vertex is given, and when an adjacent vertex is found, it moves to that adjacent vertex first and try to traverse in the same manner.

#### 33. How does dictionary work?

Dictionary is a collection that stores key-value pairs in no particular order.

#### 34. Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

If immutable, the object's hash code won’t change and it allows caching the hash code of different keys which makes the overall retrieval process very fast.

### Algorithms

#### 35. What is QuickSort? Describe the main logic of this sorting algorithm.

QuickSort is a Divide and Conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot
Technically, quick sort follows the below steps:

1. Make any element as pivot
2. Partition the array on the basis of pivot
3. Apply quick sort on left partition recursively
4. Apply quick sort on right partition recursively

## Software design

### Security

#### 36. What is OAuth2?

To begin at a high level, OAuth is not an API or a service: it’s an open standard for authorization and anyone can implement it.

More specifically, OAuth is a standard that apps can use to provide client applications with “secure delegated access”. OAuth works over HTTPS and authorizes devices, APIs, servers, and applications with access tokens rather than credentials.

#### 37. What is Basic Authentication?

Basic authentication is a simple authentication scheme built into the HTTP protocol. The client sends HTTP requests with the Authorization header that contains the word Basic followed by a space and a base64-encoded string username:password. For example, to authorize as demo / p@55w0rd the client would send.

#### 38. What is CORS, why it’s needed in browsers?

Cross-Origin Resource Sharing (CORS) is a mechanism that uses additional HTTP headers to tell browsers to give a web application running at one origin, access to selected resources from a different origin. A web application executes a cross-origin HTTP request when it requests a resource that has a different origin (domain, protocol, or port) from its own.

#### 39. How can you initialize a CSRF attack?

A CSRF attack can be initialized using a GET or POST request and can make use of an Iframe with attributes that make it invisible.

#### 40. What is JWT used for? Where to store it on client side?

JSON Web Token is a standard used to create access tokens for an application.

It works this way: the server generates a token that certifies the user identity, and sends it to the client.

The client will send the token back to the server for every subsequent request, so the server knows the request comes from a particular identity.

The token is stored in an HttpOnly cookie. The other methods are all prone to XSS attacks and as such they should be avoided. An HttpOnly cookie is not accessible from JavaScript, and is automatically sent to the origin server upon every request, so it perfectly suits the use case.

### Threaded programming

#### 41. When do you need to use threads in an application?

You need use threads when you are in this situation:

- Asynchronous operations
- Operations that can be parallelized
- Continual running background operations

#### 42. What is a daemon thread?

A daemon thread will run until it completes or until all User Threads have completed.

Daemon threads make excellent "behind the scenes" processes for things that must happen in the background but can be terminated when the application ends - garbage collection is a great example of a process that could be handled with a daemon thread. Once all User Threads complete, any daemon Threads that are still running are automatically halted and the application terminates.

#### 43. What is the difference between concurrent and parallel execution of code?

Concurrency means that an application is making progress on more than one task at the same time (concurrently).

Parallelism means that an application splits its tasks up into smaller subtasks which can be processed in parallel, for instance on multiple CPUs at the exact same time.

#### 44. What is the most important problem developers are faced when using threads?

Deadlocks (a deadlock occurs when a process or thread enters a waiting state because a requested system resource is held by another waiting process, which in turn is waiting for another resource held by another waiting process)

#### 45. In what kind of situations can deadlocks occur?

Mutual Exclusion : At least one unsharable resource - processes claim exclusive control of resources they need

Hold and Wait : Process holds one resource while waiting for another

No Preemption : Resources only released voluntarily - no interruption possible (i.e. cannot be forcefully withdrawn by another process)

Circular Wait : Circular chain of processes - each waiting for a resource held by another

#### 46. What are possible ways to prevent deadlocks from occurring?

Using the wait – die scheme method or wound – wait scheme.

#### 47. What does critical section or critical region mean in the context of concurrent programming?

In concurrent programming, concurrent accesses to shared resources can lead to unexpected or erroneous behavior, so parts of the program where the shared resource is accessed need to be protected in ways that avoid the concurrent access. This protected section is the critical section or critical region.
