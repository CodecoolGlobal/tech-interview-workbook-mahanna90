# Enterprise module (PHP branch)

## PHP Enterprise and Laravel

#### 1. What are the major differences between PHP 5 and PHP 7?

- Performance: new PHPNG engine improves the performance as much as twice with optimized memory usage
- Declaring The Return Type: PHP 7 allows programmers to declare the return type of the functions as per the expected return value
- Error Handling: PHP 7 has eased the process as it has replaced several major errors with exceptions that can be handled effortlessly. This has been achieved with the introduction of the new Engine Exception objects.
- 64-bit Support: PHP 7 is able to use native 64-bit integers as well as large files and hence, you can run applications flawlessly on 64-bit system architectures
- Anonymous Class: anonymous class is used to speed up the execution time
- New Operators: **spaceship operator** that comes with the notation <=>, t returns 0 when the operands are equal and 1 when the left side is greater than the right and -1 in case of the opposite. **null coalescing** operator denoted by double question marks (??), it is used to check whether something exists or not

#### 2. What are PSRs? Choose 1 and briefly describe it.

The PHP Standard Recommendation (PSR) is a PHP specification published by the PHP Framework Interop Group. Similar to Java Specification Request for Java, it serves the standardization of programming concepts in PHP.

1. **PSR-1** Basic Coding Standard: This section of the standard comprises what should be considered the standard coding elements that are required to ensure a high level of technical interoperability between shared PHP code.

   - Files MUST use only <?php and <?= tags.
   - Files MUST use only UTF-8 without BOM for PHP code.
   - Files SHOULD either declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but SHOULD NOT do both.
   - Namespaces and classes MUST follow an “autoloading” PSR: [PSR-0, PSR-4].
   - Class names MUST be declared in StudlyCaps.
   - Class constants MUST be declared in all upper case with underscore separators.
   - Method names MUST be declared in camelCase.

2. **PSR-3** Logger Interface: This document describes a common interface for logging libraries. The main goal is to allow libraries to receive a Psr\Log\LoggerInterface object and write logs to it in a simple and universal way

3. **PSR-4** Autoloader: This PSR describes a specification for autoloading classes from file paths. It is fully interoperable, and can be used in addition to any other autoloading specification, including PSR-0. This PSR also describes where to place files that will be autoloaded according to the specification.

#### 3. What is "dollar-dollar"? Write some examples for how to use it.

The $$x (double dollar or variable variable) is a reference variable that stores the value which can be accessed by using $ symbol before $x value.
(use variable names as string as value for other variables thus connecting the original value to the second variable)
A variable variable treats the value of another variable as its name.

Example:

```php
$real_variable = 'test';
$name = 'real_variable';
echo $$name;
```

Result:

```php
test
```

#### 4. What are the different types of arrays you can use in PHP?

An array in PHP is actually an ordered map. A map is a type that associates values to keys. This type is optimized for several different uses; it can be treated as an array, list (vector), hash table (an implementation of a map), dictionary, collection, stack, queue, and probably more. As array values can be other arrays, trees and multidimensional arrays are also possible.

1. **Numeric Arrays**: Default array index will be represented by numbers. By default array index starts from 0 and ends number of elements - 1
   Array creation examples:

   ```php
   $array = array("foo", "bar", "hello", "world");
   $array = ["foo", "bar", "hello", "world"];
   ```

2. **Associative Arrays**: Associative arrays are arrays that use named keys that you assign to them.
   Array creation examples:

   ```php
   $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

   $age['Peter'] = "35";
   $age['Ben'] = "37";
   $age['Joe'] = "43";
   ```

#### 5. What is a Trait?

PHP implements a way to reuse code called Traits.
Traits are a mechanism for code reuse in single inheritance languages such as PHP. A Trait is intended to reduce some limitations of single inheritance by enabling a developer to reuse sets of methods freely in several independent classes living in different class hierarchies. The semantics of the combination of Traits and classes is defined in a way which reduces complexity, and avoids the typical problems associated with multiple inheritance and Mixins.
A Trait is similar to a class, but only intended to group functionality in a fine-grained and consistent way. It is not possible to instantiate a Trait on its own. It is an addition to traditional inheritance and enables horizontal composition of behavior; that is, the application of class members without requiring inheritance.

#### 6. What's the difference between include() and require()? Tell 1-1 examples for both.

The include and require statements are identical, except upon failure:

- require will produce a fatal error (E_COMPILE_ERROR) and stop the script
- include will only produce a warning (E_WARNING) and the script will continue

If you want the execution to go on and show users the output, even if the include file is missing, use the include statement.
Otherwise, in case of FrameWork, CMS, or a complex PHP application coding, always use the require statement to include a key file to the flow of execution. This will help avoid compromising your application's security and integrity, just in-case one key file is accidentally missing.

#### 7. Explain what superglobals are. Name at least 3 of them.

Superglobals are built-in variables that are always available in all scopes.
Several predefined variables in PHP are "superglobals", which means they are available in all scopes throughout a script. There is no need to do global $variable; to access them within functions or methods.

1. $GLOBALS: An associative array containing references to all variables which are currently defined in the global scope of the script.
2. $\_SERVER: $\_SERVER is an array containing information such as headers, paths, and script locations. The entries in this array are created by the web server.
3. $\_REQUEST: An associative array that by default contains the contents of $\_GET, $\_POST and $\_COOKIE.
4. $\_GET: An associative array of variables passed to the current script via the URL parameters (aka. query string).
5. $\_POST: An associative array of variables passed to the current script via the HTTP POST method when using application/x-www-form-urlencoded or multipart/form-data as the HTTP Content-Type in the request.
6. $\_SESSION: An associative array containing session variables available to the current script.
7. $\_COOKIE: An associative array of variables passed to the current script via HTTP Cookies.
8. $\_FILES: An associative array of items uploaded to the current script via the HTTP POST method.
9. $\_ENV: An associative array of variables passed to the current script via the environment method.

#### 8. What are magic methods?

Magic methods are special methods which override PHP's default's action when certain actions are performed on an object.
The following method names are considered magical:
\_\_construct(), \_\_destruct(), \_\_call(), \_\_callStatic(), \_\_get(), \_\_set(), \_\_isset(), \_\_unset(), \_\_sleep(), \_\_wakeup(), \_\_serialize(), \_\_unserialize(), \_\_toString(), \_\_invoke(), \_\_set_state(), \_\_clone(), and \_\_debugInfo().
All magic methods, with the exception of \_\_construct(), \_\_destruct(), and \_\_clone(), must be declared as public, otherwise an E_WARNING is emitted.

#### 9. How to read the content of a file in PHP?

Example #1:

```php
<?php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fread($myfile,filesize("webdictionary.txt"));
fclose($myfile);
?>
```

Example #2:

```php
<?php
// READ ENTIRE CONTENTS INTO A STRING
$text = file_get_contents('README.txt');
echo $text;
```

Example #3:

```php
<?php
// FILE TO ARRAY
$array = file('README.txt');
print_r($array);

// ADDITIONAL OPTION - SKIP EMPTY LINES
$array = file('README.txt', FILE_SKIP_EMPTY_LINES);
print_r($array);
```

Example #4:

```php
<?php
// (A) OPEN FILE
$handle = fopen("README.txt", "r") or die("Error reading file!");

// (B) READ LINE BY LINE
while (($line = fgets($handle)) !== false) {
// To better manage the memory, you can also specify how many bytes to read at once
// while (($line = fgets($handle, 4096)) !== false) {
  echo $line;
}

// (C) CLOSE FILE
fclose($handle);
```

#### 10. What is .htaccess?

An .htaccess (hypertext access) file is a directory-level configuration file supported by several web servers, used for configuration of website-access issues, such as URL redirection, URL shortening, access control (for different web pages and files), and more.
An .htaccess files provide a way to make configuration changes on a per-directory basis.
.htaccess files act as a subset of the server's global configuration file (like httpd.conf) for the directory that they are in, or all sub-directories.

In general, .htaccess files use the same syntax as the main configuration files. What you can put in these files is determined by the AllowOverride directive. This directive specifies, in categories, what directives will be honored if they are found in a .htaccess file. If a directive is permitted in a .htaccess file, the documentation for that directive will contain an Override section, specifying what value must be in AllowOverride in order for that directive to be permitted.

Content example:

```json
<Files "config.json">
    Order Deny,Allow
    Deny from all
</Files>
```

#### 11. What are the key differences between Errors and Exceptions?

Exceptions are thrown - they are intended to be caught and program execution will continue. Errors are generally unrecoverable, program execution stops.

**Error**: An Error is an unexpected program result, which can not be handled by the program itself. That can be solved by using the issue in the code manually. An Error can be an infinite loop that can not be handled by the program itself so you have to manually repair that issue. There is an easy procedure to handle error i.e. using die() function.

Example:

```php
<?php

// Open file in read mode
$file_var = fopen("myfile.txt", "r");

// Check for file existence
if (!file_exists("myfile.txt")) {
    die("Sorry Error!! file does not exists");
}
else {
    fopen("myfile.txt", "r");
}

?>
```

**Exception**: An Exception also is an unexpected result of a program but Exception can be handled by the program itself by throwing another exception. Exceptions should only be used with error conditions, where the error is non removal. There is an easy way to overcome the Exception by using try and catch method.

Example:

```php
<?php

function valid_division($x, $y) {

    if($y != 0) {
        return true;
    }
    else {
        throw new Exception("Why should not be equal to 0");
    }
}

try {
    valid_division(2, 0);

    // Try block will only run if
    // there is no exception
    echo "Valid division";
}
catch(Exception $e) {

    // Catch block will run if an
    // exception occurs
    echo "Error\n";
    echo $e->getmessage();
}

?>
```

#### 12. What is the difference between .php and .phar files?

A file with the **.php** file extension is a plain-text file that contains the source code written in the PHP (it’s a recursive acronym meaning PHP: Hypertext Preprocessor) programming language. Can be opened in any test editor.\
The **.phar** extension provides a way to put entire PHP applications into a single file called a "phar" (PHP Archive) for easy distribution and installation. Phar archives are best characterized as a convenient way to group several files into a single file. As such, a phar archive provides a way to distribute a complete PHP application in a single file and run it from that file without the need to extract it to disk. Additionally, phar archives can be executed by PHP as easily as any other file, both on the commandline and from a web server. Phar is kind of like a thumb drive for PHP applications.

#### 13. What is Laravel? What are its main advantages?

Laravel is a free, open-source PHP web framework, created by Taylor Otwell and intended for the development of web applications following the model–view–controller (MVC) architectural pattern and based on Symfony.

1. Creating authorization and authentication systems
2. Integration with tools to make faster web apps
3. Mail services integration
4. Handling exception and configuration error (integrated with the Monolog logging library )
5. Automation testing work (esting with PHPUnit is included out-of-the-box. It also ships with convenient helper methodologies, enabling expressive testing of apps)
6. Separation of business logic code from presentation code
7. Fixing most common technical vulnerabilities
8. Scheduling tasks configuration and management
9. Enabling you to create and set up multiple cache configurations, the framework fully support cache backends like Redis or Memcached.
10. Artisan (its own integrated command-line interface)
11. MVC: Laravel is an MVC framework, which means that developers don’t need to use the old methods of writing entire PHP and PHP codes in the same files
12. Reverse routing
13. Queue management
14. Eloquent ORM (create models which have a corresponding table in the database.)

#### 14. What is Artisan?

Artisan is the command line interface included with Laravel. Artisan exists at the root of your application as the artisan script and provides a number of helpful commands that can assist you while you build your application.\
It has got a robust list of commands which make life easier for the developer and save a lot of time. The other advantage that Artisan provides is custom command which is available to developer on top of the inclusive commands inherent to it. Developers can generate migrations, publish assets of packages and many similar tasks.

#### 15. What is the purpose of Middlewares in Laravel?

Middleware acts as a bridge between a request and a response. It is a type of filtering mechanism.\
Laravel includes a middleware that verifies whether the user of the application is authenticated or not. If the user is authenticated, it redirects to the home page otherwise, if not, it redirects to the login page. The most common example is auth middleware which checks if the current user is logged in or not.\
Middleware can be created by executing the following command:

```php
php artisan make:middleware <middleware-name>
```

There is another middleware name CORS in charge of adding appropriate headers to all of your responses.

Example with Sanctum as middleware:

```php
Route::group(['middleware' => 'auth:sanctum'], function () {
    Route::post('addToFavourites', [FavouritesController::class, 'addToFavourites']);
    Route::post('getFavouritesOfUser', [FavouritesController::class, 'getFavouritesOfUser']);
});
```

#### 16. What are service providers in Laravel?

Service providers are the central place of all Laravel application bootstrapping. Your own application, as well as all of Laravel's core services, are bootstrapped via service providers.

If you open the config/app.php file included with Laravel, you will see a providers array. These are all of the service provider classes that will be loaded for your application. By default, a set of Laravel core service providers are listed in this array.

These providers bootstrap the core Laravel components, such as the mailer, queue, cache, auth, and others. Many of these providers are "deferred" providers, meaning they will not be loaded on every request, but only when the services they provide are actually needed.

#### 17. What is Composer used for? What should you do to make it work? Write some real-life examples.

Composer is a tool for dependency management in PHP. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.\
Composer is not a package manager in the same sense as Yum or Apt are. Yes, it deals with "packages" or libraries, but it manages them on a per-project basis, installing them in a directory (e.g. vendor) inside your project. By default, it does not install anything globally.

Usage:

1. Install composer
2. Create composer.json file
3. Install dependencies by require or by composer install (update) (this also generates the composer.lock file with the installed details)

Composer.json file content example:

```json
{
  "name": "laravel/laravel",
  "type": "project",
  "description": "The Laravel Framework.",
  "keywords": ["framework", "laravel"],
  "license": "MIT",
  "require": {
    "php": "^7.3|^8.0",
    "fideloper/proxy": "^4.4",
    "fruitcake/laravel-cors": "^2.0",
    "guzzlehttp/guzzle": "^7.0.1",
    "laravel/framework": "^8.12",
    "laravel/sanctum": "^2.9",
    "laravel/tinker": "^2.5",
    "ext-curl": "*",
    "ext-json": "*"
  },
  "autoload": {
    "psr-4": {
      "App\\": "app/",
      "Database\\Factories\\": "database/factories/",
      "Database\\Seeders\\": "database/seeders/"
    }
  }
}
```

The autoload section contains the namespaces used in the project, the require section contains the dependencies to be installed.

#### 18. What are the major differences between PEAR, Composer and PECL?

**PECL**: (PHP Extension Community Library) PECL is a repository for php extensions, You can download and install any php extension available from their repository. Using PECL you can install old php extensions, if you are not able to install those extensions from ubuntu repository.

**PEAR**: (PHP Extension and Application Repository) PEAR is a distribution system for reusable PHP libraries or classes. Soon going to be deprecated.

**COMPOSER**: Composer is a dependency management tool in php. You can use composer in your own project to manage external libraries and dependencies.

#### 19. What does a composer.json file contain?

App name, type, description, licence, required dependencies with accepted versions, autoload section for namespaces.
Example:

```json
{
  "name": "laravel/laravel",
  "type": "project",
  "description": "The Laravel Framework.",
  "keywords": ["framework", "laravel"],
  "license": "MIT",
  "require": {
    "php": "^7.3|^8.0",
    "fideloper/proxy": "^4.4",
    "fruitcake/laravel-cors": "^2.0",
    "guzzlehttp/guzzle": "^7.0.1",
    "laravel/framework": "^8.12",
    "laravel/sanctum": "^2.9",
    "laravel/tinker": "^2.5",
    "ext-curl": "*",
    "ext-json": "*"
  },
  "autoload": {
    "psr-4": {
      "App\\": "app/",
      "Database\\Factories\\": "database/factories/",
      "Database\\Seeders\\": "database/seeders/"
    }
  }
}
```

## Object Relational Mapping

#### 20. What is an ORM? What are the benefits, when to use?

Object-relational-mapping is the idea of being able to write queries, using the object-oriented paradigm of your preferred programming language. We are trying to interact with our database using our language of choice instead of SQL. Makes migration easier because it is not sql type specific.

Pros:

1. You get to write in the language you are already using anyway.
2. It abstracts away the database system so that switching DB is easy.
3. Depending on the ORM you get a lot of advanced features out of the box, such as support for transactions, connection pooling, migrations, seeds, streams
4. Many of the queries you write will perform better than if you wrote them yourself

Cons:

1. There is overhead involved in learning how to use any given ORM
2. If you are a master at SQL, you can probably get more performant queries by writing them yourself
3. The initial configuration of an ORM can be a headache.
4. As a developer, it is important to understand what is happening under the hood.

#### 21. What is Eloquent? What are the advantages, limitations?

Laravel includes Eloquent, an object-relational mapper (ORM) that makes it enjoyable to interact with your database. When using Eloquent, each database table has a corresponding "Model" that is used to interact with that table. In addition to retrieving records from the database table, Eloquent models allow you to insert, update, and delete records from the table as well.

Models typically live in the app\Models directory and extend the Illuminate\Database\Eloquent\Model class. You may use the make:model Artisan command to generate a new model.

All Eloquent models extends from the Eloquent class. The lower-case, plural name of the class will be used as the table name unless another name is explicitly specified. Eloquent will also assume that each table has a primary key column named “id” unless specified.

src: https://webkul.com/blog/laravel-query-builder-eloquent-orm/

StackOverflow explanation:
Active Record is a good solution for processing a single entity in CRUD manner - that is, create a new entity with filled properties and then save it to a database, load a record from a database, or delete.

You will benefit a lot from Eloquent's features such as dirty checking (to send SQL UPDATE only for the fields which have been changed), model events (e.g. to send administrative alerts or update statistics counters when someone has created a new account), traits (timestamps, soft deletes, your custom traits) eager/lazy loading etc. You can also apply domain-driven pattern and implement some pieces of business logic in your Active Record entities, for example, validation, managing relations, calculations etc.

But, as you already know, Active Record comes with some performance price.

When you process a single record or a few records, there is nothing to worry about. But for cases when you read lots of records (e.g. for datagrids, for reports, for batch processing etc.) the plain Laravel DB methods is a better approach.

For our Laravel based applications we are using both approaches as we see appropriate. We use Laravel's Eloquent for UI forms to process a single record and use DB methods (backed by SQL views with additional database engine specific performance tweaks) to retrieve data for UI tables, export tasks etc. It also works well with RESTful APIs - Eloquent for GET, PUT, POST, DELETE with a key and DB for GET without key but with filters and sorting and paging.

#### 22. What is the difference between PDO and Eloquent? Which are the advantages and disadvantages of each?

The PHP Data Objects (PDO) extension defines a lightweight, consistent interface for accessing databases in PHP. Each database driver that implements the PDO interface can expose database-specific features as regular extension functions. PDO provides a data-access abstraction layer, which means that, regardless of which database you're using, you use the same functions to issue queries and fetch data. PDO does not provide a database abstraction. PDO is a library that uses mysqli, but makes it easier for you to write prepared statements. Can be more efficient than ORM.

Eloquent abstracts away the database system, there is no need to write queries in SQL, but it is also slower. It has the benefit that if the db is changed, the queries don't need to be rewritten in a different SQL dialect.

#### 23. What are migrations? Why are they important?

Migrations are like version control for your database, allowing your team to define and share the application's database schema definition.

You may use the make:migration Artisan command to generate a database migration. The new migration will be placed in your database/migrations directory.

Laravel will use the name of the migration to attempt to guess the name of the table and whether or not the migration will be creating a new table.

If you have ever had to tell a teammate to manually add a column to their local database schema after pulling in your changes from source control, you've faced the problem that database migrations solve.

#### 24. Name 3 aggregate methods provided by query builder in Laravel. What can they do for you?

Count: count of an element\
Max: max value\
Min: min value\
Sum: sum of value\
Avg: average of values

```php
<?php

use App\Product;

$count = Product::where('active', 1)->count();
$max = Product::where('active', 1)->max('price');
$min = Product::where('active', 1)->min('price');
$sum = Product::where('active', 1)->sum('price');
$avg = Product::where('active', 1)->avg('price');
```

#### 25. What is a Model Observer?

Laravel implements Observer Pattern to fire some events, which can be listened to hook into, when various actions are performed on a model.\
The observer pattern is a software design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.\
Eloquent provides a handful of events to monitor the model state, like: creating, created, saving, deleting, restoring etc.\
Using model observers, you can group all your events into a single class. All method names in the observer class will reflect on the event you are listening to.

There are some limitations attached to Model Observer which you should keep in mind while using the model observers.

- When you use saved or saving hooks, you should never call the model’s save method.
- If you are using saved hook and want to call the save method, then you should probably use the saving hook.
- If your logic need to call model’s save method, then rethink your logic or avoid using observers.

src: https://www.larashout.com/how-to-use-laravel-model-observers

#### 26. How would you define Eloquent Collections?

All multi-result sets returned by Eloquent are instances of the Illuminate\Database\Eloquent\Collection object, including results retrieved via the get method or accessed via a relationship. The Eloquent collection object extends the Laravel base collection, so it naturally inherits dozens of methods used to fluently work with the underlying array of Eloquent models. Collections are much more powerful than arrays and expose a variety of map / reduce operations that may be chained using an intuitive interface. All collections also serve as iterators, allowing you to loop over them as if they were simple PHP arrays.

Inherited methods: contains, diff, excep, find, fresh, intersect, load, loadMissing, modelKeys, makeVisible, makeHidden, only, toQuery, unique

#### 27. What are Polymorphic Relationships? Name a few of them.

A polymorphic relationship is where a model can belong to more than one other model on a single association. (one to one, one to many, many to many)

Let’s create an imaginary situation where we have a Topic and a Post model. Users can leave comments on both topics and posts. Using polymorphic relationships, we can use a single comments table for both of these scenarios. Surprising, yeah? This seems a bit impractical since, ideally, we’d have to create a post_comments table and a topic_comments table to differentiate the comments. With polymorphic relationships, we don’t need two tables.
