
# review

# RESTful web API design 

* ## What is REST?

In 2000, Roy Fielding proposed Representational State Transfer (REST) as an architectural approach to designing web services. REST is an architectural style for building distributed systems based on hypermedia. REST is independent of any underlying protocol and is not necessarily tied to HTTP. However, most common REST API implementations use HTTP as the application protocol, and this guide focuses on designing REST APIs for HTTP.

A primary advantage of REST over HTTP is that it uses open standards, and does not bind the implementation of the API or the client applications to any specific implementation. For example, a REST web service could be written in ASP.NET, and client applications can use any language or toolset that can generate HTTP requests and parse HTTP responses.

Here are some of the main design principles of RESTful APIs using HTTP:

* REST APIs are designed around resources, which are any kind of object, data, or service that can be accessed by the client.

* A resource has an identifier, which is a URI that uniquely identifies that resource. For example, the URI for a particular customer order might be:

> HTTP

> https://adventure-works.com/orders/1

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

**Level 3 corresponds to a truly RESTful API according to Fielding's definition. In practice, many published web APIs fall somewhere around level 2.**


> Adopt a consistent naming convention in URIs. In general, it helps to use plural nouns for URIs that reference collections. It's a good practice to organize URIs for collections and items into a hierarchy. For example, `/customers` is the path to the customers collection, and `/customers/5` is the path to the customer with ID equal to 5. This approach helps to keep the web API intuitive. Also, many web API frameworks can route requests based on parameterized URI paths, so you could define a route for the path `/customers/{id}`.


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

* A PUT request creates a resource or updates an existing resource. The client specifies the URI for the resource. The request body contains a complete representation of the resource. If a resource with this URI already exists, it is replaced. Otherwise a new resource is created, if the server supports doing so. PUT requests are most frequently applied to resources that are individual items, such as a specific customer, rather than collections. A server might support updates but not creation via PUT. Whether to support creation via PUT depends on whether the client can meaningfully assign a URI to a resource before it exists. If not, then use POST to create resources and PUT or PATCH to update.

* A PATCH request performs a partial update to an existing resource. The client specifies the URI for the resource. The request body specifies a set of changes to apply to the resource. This can be more efficient than using PUT, because the client only sends the changes, not the entire representation of the resource. Technically PATCH can also create a new resource (by specifying a set of updates to a "null" resource), if the server supports this.


* ## Conform to HTTP semantics

This section describes some typical considerations for designing an API that conforms to the HTTP specification. However, it doesn't cover every possible detail or scenario. When in doubt, consult the HTTP specifications.

### Media types

As mentioned earlier, clients and servers exchange representations of resources. For example, in a POST request, the request body contains a representation of the resource to create. In a GET request, the response body contains a representation of the fetched resource.

In the HTTP protocol, formats are specified through the use of media types, also called MIME types. For non-binary data, most web APIs support JSON (media type = application/json) and possibly XML (media type = application/xml).

The Content-Type header in a request or response specifies the format of the representation. Here is an example of a POST request that includes JSON data:

> HTTP

> POST https://adventure-works.com/orders HTTP/1.1
> Content-Type: application/json; charset=utf-8
> Content-Length: 57

>`{"Id":1,"Name":"Gizmo","Category":"Widgets","Price":1.99}`

If the server doesn't support the media type, it should return HTTP status code 415 (Unsupported Media Type).

A client request can include an Accept header that contains a list of media types the client will accept from the server in the response message. For example:

> HTTP

> GET `https://adventure-works.com/orders/2 HTTP/1.1`
> Accept: `application/json`

If the server cannot match any of the media type(s) listed, it should return HTTP status code 406 (Not Acceptable).

### GET methods

A successful GET method typically returns HTTP status code 200 (OK). If the resource cannot be found, the method should return 404 (Not Found).

### POST methods

If a POST method creates a new resource, it returns HTTP status code 201 (Created). The URI of the new resource is included in the Location header of the response. The response body contains a representation of the resource.

If the method does some processing but does not create a new resource, the method can return HTTP status code 200 and include the result of the operation in the response body. Alternatively, if there is no result to return, the method can return HTTP status code 204 (No Content) with no response body.

If the client puts invalid data into the request, the server should return HTTP status code 400 (Bad Request). The response body can contain additional information about the error or a link to a URI that provides more details.



### PATCH methods

> With a PATCH request, the client sends a set of updates to an existing resource, in the form of a patch document. The server processes the patch document to perform the update. The patch document doesn't describe the whole resource, only a set of changes to apply. The specification for the PATCH method (RFC 5789) doesn't define a particular format for patch documents. The format must be inferred from the media type in the request.



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

Sometimes a POST, PUT, PATCH, or DELETE operation might require processing that takes a while to complete. If you wait for completion before sending a response to the client, it may cause unacceptable latency. If so, consider making the operation asynchronous. Return HTTP status code 202 (Accepted) to indicate the request was accepted for processing but is not completed.

You should expose an endpoint that returns the status of an asynchronous request, so the client can monitor the status by polling the status endpoint. Include the URI of the status endpoint in the Location header of the 202 response. For example:

> HTTP

> HTTP/1.1 202 Accepted

> Location: /api/status/12345

If the client sends a GET request to this endpoint, the response should contain the current status of the request. Optionally, it could also include an estimated time to completion or a link to cancel the operation.

> HTTP

> HTTP/1.1 200 OK

> Content-Type: application/json

>{

>    "status":"In progress",

>    "link": `{ "rel":"cancel", "method":"delete", "href":"/api/status/12345" }`

>}

If the asynchronous operation creates a new resource, the status endpoint should return status code 303 (See Other) after the operation completes. In the 303 response, include a Location header that gives the URI of the new resource:

> HTTP

> HTTP/1.1 303 See Other

> Location: /api/orders/12345
