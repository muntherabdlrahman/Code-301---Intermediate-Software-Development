
# review

## RESTful web API design 

### What is REST?



Here are some of the main design principles of RESTful APIs using HTTP:

* REST APIs are designed around resources, which are any kind of object, data, or service that can be accessed by the client.

* A resource has an identifier, which is a URI that uniquely identifies that resource. For example, the URI for a particular customer order might be:

* Clients interact with a service by exchanging representations of resources. Many web APIs use JSON as the exchange format. For example, a GET request to the URI listed above might return this response body:

> JSON

> `{"orderId":1,"orderValue":99.90,"productId":1,"quantity":1}`

* REST APIs use a uniform interface, which helps to decouple the client and service implementations. For REST APIs built on HTTP, the uniform interface includes using standard HTTP verbs to perform operations on resources. The most common operations are GET, POST, PUT, PATCH, and DELETE.

* REST APIs use a stateless request model. HTTP requests should be independent and may occur in any order, so keeping transient state information between requests is not feasible. The only place where information is stored is in the resources themselves, and each request should be an atomic operation. This constraint enables web services to be highly scalable, because there is no need to retain any affinity between clients and specific servers. Any server can handle any request from any client. That said, other factors can limit scalability. For example, many web services write to a backend data store, which may be hard to scale out.


* REST APIs are driven by hypermedia links that are contained in the representation. For example, the following shows a JSON representation of an order. It contains links to get or update the customer associated with the order.

In 2008, Leonard Richardson proposed the following maturity model for web APIs:

* Level 0: Define one URI, and all operations are POST requests to this URI.

* Level 1: Create separate URIs for individual resources.

* Level 2: Use HTTP methods to define operations on resources.

* Level 3: Use hypermedia .

Level 3 corresponds to a truly RESTful API according to Fielding's definition. In practice, many published web APIs fall somewhere around level 2.

* ## Organize the API design around resources .

***Focus on the business entities that the web API exposes. For example, in an e-commerce system, the primary entities might be customers and orders. Creating an order can be achieved by sending an HTTP POST request that contains the order information. The HTTP response indicates whether the order was placed successfully or not. When possible, resource URIs should be based on nouns (the resource) and not verbs (the operations on the resource).***



***A resource doesn't have to be based on a single physical data item. For example, an order resource might be implemented internally as several tables in a relational database, but presented to the client as a single entity. Avoid creating APIs that simply mirror the internal structure of a database. The purpose of REST is to model entities and the operations that an application can perform on those entities. A client should not be exposed to the internal implementation.***

Sending an HTTP GET request to the collection URI retrieves a list of items in the collection. Each item in the collection also has its own unique URI. An HTTP GET request to the item's URI returns the details of that item.

Adopt a consistent naming convention in URIs. In general, it helps to use plural nouns for URIs that reference collections. It's a good practice to organize URIs for collections and items into a hierarchy. For example, `/customers` is the path to the customers collection, and `/customers/5` is the path to the customer with ID equal to 5. This approach helps to keep the web API intuitive. Also, many web API frameworks can route requests based on parameterized URI paths, so you could define a route for the path `/customers/{id}`.

Also consider the relationships between different types of resources and how you might expose these associations. For example, the `/customers/5/orders` might represent all of the orders for customer 5. You could also go in the other direction, and represent the association from an order back to a customer with a URI such as `/orders/99/customer`. However, extending this model too far can become cumbersome to implement. A better solution is to provide navigable links to associated resources in the body of the HTTP response message. This mechanism is described in more detail in the section Use HATEOAS to enable navigation to related resources.

In more complex systems, it can be tempting to provide URIs that enable a client to navigate through several levels of relationships, such as `/customers/1/orders/99/products`. However, this level of complexity can be difficult to maintain and is inflexible if the relationships between resources change in the future. Instead, try to keep URIs relatively simple. Once an application has a reference to a resource, it should be possible to use this reference to find items related to that resource. The preceding query can be replaced with the URI `/customers/1/orders` to find all the orders for customer 1, and then `/orders/99/products` to find the products in this order.

Another factor is that all web requests impose a load on the web server. The more requests, the bigger the load. Therefore, try to avoid "chatty" web APIs that expose a large number of small resources. Such an API may require a client application to send multiple requests to find all of the data that it requires. Instead, you might want to denormalize the data and combine related information into bigger resources that can be retrieved with a single request. However, you need to balance this approach against the overhead of fetching data that the client doesn't need. Retrieving large objects can increase the latency of a request and incur additional bandwidth costs.

Avoid introducing dependencies between the web API and the underlying data sources. For example, if your data is stored in a relational database, the web API doesn't need to expose each table as a collection of resources. In fact, that's probably a poor design. Instead, think of the web API as an abstraction of the database. If necessary, introduce a mapping layer between the database and the web API. That way, client applications are isolated from changes to the underlying database scheme.

Finally, it might not be possible to map every operation implemented by a web API to a specific resource. You can handle such non-resource scenarios through HTTP requests that invoke a function and return the results as an HTTP response message. For example, a web API that implements simple calculator operations such as add and subtract could provide URIs that expose these operations as pseudo resources and use the query string to specify the parameters required. For example, a GET request to the URI `/add?operand1=99&operand2=1` would return a response message with the body containing the value 100. However, only use these forms of URIs sparingly.

* ## Define API operations in terms of HTTP methods

The HTTP protocol defines a number of methods that assign semantic meaning to a request. The common HTTP methods used by most RESTful web APIs are:

* GET retrieves a representation of the resource at the specified URI. The body of the response message contains the details of the requested resource.

* POST creates a new resource at the specified URI. The body of the request message provides the details of the new resource. Note that POST can also be used to trigger operations that don't actually create resources.

* PUT either creates or replaces the resource at the specified URI. The body of the request message specifies the resource to be created or updated.

* PATCH performs a partial update of a resource. The request body specifies the set of changes to apply to the resource.

* DELETE removes the resource at the specified URI.

The effect of a specific request should depend on whether the resource is a collection or an individual item. The following table summarizes the common conventions adopted by most RESTful implementations using the e-commerce example. Not all of these requests might be implemented—it depends on the specific scenario.

Resource|POST|GET|PUT|DELETE
-|-|-|-|-
/customers|Create a new customer|Retrieve all customers|Bulk update of customers|Remove all customers
-|-|-|-|-
/customers/1|Error|Retrieve the details for customer 1|Update the details of customer 1 if it exists|Remove customer 1
-|-|-|-|-
/customers/1/orders |	Create a new order for customer 1 	|Retrieve all orders for customer 1 |	Bulk update of orders for customer 1 |	Remove all orders for customer 1


The differences between POST, PUT, and PATCH can be confusing.

* A POST request creates a resource. The server assigns a URI for the new resource, and returns that URI to the client. In the REST model, you frequently apply POST requests to collections. The new resource is added to the collection. A POST request can also be used to submit data for processing to an existing resource, without any new resource being created.



Error condition |	HTTP status code
-|-
The patch document format isn't supported. |	415 (Unsupported Media Type)
-|-
Malformed patch document. |	400 (Bad Request)
-|-
The patch document is valid, but the changes can't be applied to the resource in its current state. |	409 (Conflict)

### DELETE methods

If the delete operation is successful, the web server should respond with HTTP status code 204, indicating that the process has been successfully handled, but that the response body contains no further information. If the resource doesn't exist, the web server can return HTTP 404 (Not Found).

### Asynchronous operations

> HTTP

> HTTP/1.1 202 Accepted

> Location: /api/status/12345

#### If the client sends a GET request to this endpoint, the response should contain the current status of the request. Optionally, it could also include an estimated time to completion or a link to cancel the operation.

> HTTP

> HTTP/1.1 200 OK

> Content-Type: application/json

>{

>    "status":"In progress",

>    "link": `{ "rel":"cancel", "method":"delete", "href":"/api/status/12345" }`

>}

**If the asynchronous operation creates a new resource, the status endpoint should return status code 303 (See Other) after the operation completes. In the 303 response, include a Location header that gives the URI of the new resource:**

> HTTP

> HTTP/1.1 303 See Other

> Location: /api/orders/12345

 ## Filter and paginate data

***Exposing a collection of resources through a single URI can lead to applications fetching large amounts of data when only a subset of the information is required. For example, suppose a client application needs to find all orders with a cost over a specific value. It might retrieve all orders from the /orders URI and then filter these orders on the client side. Clearly this process is highly inefficient. It wastes network bandwidth and processing power on the server hosting the web API.***



> HTTP

>/orders?limit=25&offset=50

 ***consider imposing an upper limit on the number of items returned, to help prevent Denial of Service attacks. To assist client applications, GET requests that return paginated data should also include some form of metadata that indicate the total number of resources available in the collection.***



# Concepts of Functional Programming in Javascript

What is functional programming?

Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — Wikipedia

## Pure functions

The first fundamental concept we learn when we want to understand functional programming is pure functions. But what does that really mean? What makes a function pure?

Here is a very strict definition of purity:

* It returns the same result if given the same arguments (it is also referred as deterministic)

* It does not cause any observable side effects

### It returns the same result if given the same arguments

Imagine we want to implement a function that calculates the area of a circle. An impure function would receive radius as the parameter, and then calculate radius * radius * PI:

> `let PI = 3.14;`

> `const calculateArea = (radius) => radius * radius * PI;`

> `calculateArea(10); // returns 314.0`

Why is this an impure function? Simply because it uses a global object that was not passed as a parameter to the function.

Now imagine some mathematicians argue that the PI value is actually 42and change the value of the global object.

Our impure function will now result in 10 * 10 * 42 = 4200. For the same parameter (radius = 10), we have a different result. Let's fix it!

> `let PI = 3.14;`

> `const calculateArea = (radius, pi) => radius * radius * pi;`

> `calculateArea(10, PI); // returns 314.0`

Now we’ll always pass thePI value as a parameter to the function. So now we are just accessing parameters passed to the function. No external object.

* For the parameters radius = 10 & PI = 3.14, we will always have the same the result: 314.0

* For the parameters radius = 10 & PI = 42, we will always have the same the result: 4200

### Reading Files

If our function reads external files, it’s not a pure function — the file’s contents can change.

`const charactersCounter = (text) => ``Character count: ${text.length}`;

> `function analyzeFile(filename) {`

>  `let fileContent = open(filename);`

> ` return charactersCounter(fileContent);`

>`}`

### Random number generation

Any function that relies on a random number generator cannot be pure.

> `function yearEndEvaluation() {`

>  `if (Math.random() > 0.5) {`

>   ` return "You get a raise!";`

>  `} else {`

>   ` return "Better luck next year!";`

>  `}`

>`}`

### It does not cause any observable side effects

Examples of observable side effects include modifying a global object or a parameter passed by reference.

> `let counter = 1;`

> `function increaseCounter(value) {`

> `  counter = value + 1;`

> `}`

> `increaseCounter(counter);`

> `console.log(counter); // 2`

We have the counter value. Our impure function receives that value and re-assigns the counter with the value increased by 1.

Observation: mutability is discouraged in functional programming.

We are modifying the global object. But how would we make it pure? Just return the value increased by 1. Simple as that.

> `let counter = 1;`

> `const increaseCounter = (value) => value + 1;`

> `increaseCounter(counter); // 2`

> `console.log(counter); // 1`

See that our pure function increaseCounter returns 2, but the counter value is still the same. The function returns the incremented value without altering the value of the variable.

If we follow these two simple rules, it gets easier to understand our programs. Now every function is isolated and unable to impact other parts of our system.

Pure functions are stable, consistent, and predictable. Given the same parameters, pure functions will always return the same result. We don’t need to think of situations when the same parameter has different results — because it will never happen.

Pure functions benefits

The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts:

* Given a parameter A → expect the function to return value B

* Given a parameter C → expect the function to return value D

## Immutability

> * Unchanging over time or unable to be changed.

When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.

In Javascript we commonly use the for loop. This next for statement has some mutable variables.

> `var values = [1, 2, 3, 4, 5];`

> `var sumOfValues = 0;`

> `for (var i = 0; i < values.length; i++) {`

> `  sumOfValues += values[i];`

> `}`

> `sumOfValues // 15`

For each iteration, we are changing the i and the sumOfValue state. But how do we handle mutability in iteration? Recursion!

> `let list = [1, 2, 3, 4, 5];`

> `let accumulator = 0;`

> `function sum(list, accumulator) {`

> `  if (list.length == 0) {`

> `    return accumulator;`

> `  }`

> `  return sum(list.slice(1), accumulator + list[0]);`

> `}`

> `sum(list, accumulator); // 15`

> `list; // [1, 2, 3, 4, 5]`

>`accumulator; // 0`

So here we have the sum function that receives a vector of numerical values. The function calls itself until we get the list empty (our recursion base case). For each "iteration" we will add the value to the total accumulator.

With recursion, we keep our variables immutable. The list and the accumulator variables are not changed. It keeps the same value.

Observation: Yes! We can use reduce to implement this function. We will cover this in the Higher Order Functions topic.

It is also very common to build up the final state of an object. Imagine we have a string, and we want to transform this string into a url slug.

In OOP in Ruby, we would create a class, let’s say, UrlSlugify. And this class will have a slugify! method to transform the string input into a url slug.

## Referential transparency

Let’s implement a square function:

> `const square = (n) => n * n;`

This pure function will always have the same output, given the same input.

Passing 2 as a parameter of the square function will always returns 4. So now we can replace the square(2) with 4. That's it! Our function is referentially transparent.

Basically, if a function consistently yields the same result for the same input, it is referentially transparent.

pure functions + immutable data = referential transparency

With this concept, a cool thing we can do is to memoize the function. Imagine we have this function:

> `const sum = (a, b) => a + b;`

And we call it with these parameters:

> `sum(3, sum(5, 8));`

The sum(5, 8) equals 13. This function will always result in 13. So we can do this:

> `sum(3, 13);`

And this expression will always result in 16. We can replace the entire expression with a numerical constant and memoize it.

## Functions as first-class entities

The idea of functions as first-class entities is that functions are also treated as values and used as data.

Functions as first-class entities can:

* refer to it from constants and variables

* pass it as a parameter to other functions

* return it as result from other functions

The idea is to treat functions as values and pass functions like data. This way we can combine different functions to create new functions with new behavior.

Imagine we have a function that sums two values and then doubles the value. Something like this:

> `const doubleSum = (a, b) => (a + b) * 2;`

Now a function that subtracts values and the returns the double:

> `const doubleSubtraction = (a`, b) => (a - b) * 2;

These functions have similar logic, but the difference is the operators functions. If we can treat functions as values and pass these as arguments, we can build a function that receives the operator function and use it inside our function.

## Higher-order functions

When we talk about higher-order functions, we mean a function that either:

* takes one or more functions as arguments, or

* returns a function as its result

The doubleOperator function we implemented above is a higher-order function because it takes an operator function as an argument and uses it.

You’ve probably already heard about filter, map, and reduce. Let's take a look at these.

### Filter

Given a collection, we want to filter by an attribute. The filter function expects a true or false value to determine if the element should or should not be included in the result collection. Basically, if the callback expression is true, the filter function will include the element in the result collection. Otherwise, it will not.


