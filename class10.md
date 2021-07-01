

# The JavaScript Call Stack 

![mmmkm](https://miro.medium.com/max/1592/0*ryPdDzB_jghiVi2e.png)

***The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers.***

### What is The call stack ??

> ***The call stack is primarily used for function invocation (call). Since the call stack is single, function(s) execution, is done, one at a time, from top to bottom. It means the call stack is synchronous.***



* In Asynchronous JavaScript, we have a callback function, an event loop, and a task queue. The callback function is acted upon by the call stack during execution after the call back function has been pushed to the stack by the event loop.

### But before we jump the gun, let us first attempt to answer the question - What is the call stack?


> ***operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.***



* Temporarily store: When a function is invoked (called), the function, its parameters, and variables are pushed into the call stack to form a stack frame. This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.


* Manage function invocation (call): The call stack maintains a record of the position of each stack frame. It knows the next function to be executed (and will remove it after execution). This is what makes code execution in JavaScript synchronous.

### Think of yourself standing on a queue, in a grocery store cash point. You can only be attended to after the person in front of you have been attended to. That’s synchronous.

`This is what we mean by “manage function invocation”.!!`


### what happens when the code is run? 

1. When secondFunction() gets executed, an empty stack frame is created. It is the main (anonymous) entry point of the program.
2. secondFunction() then calls firstFunction()which is pushed into the stack.
3. firstFunction() returns and prints “Hello from firstFunction” to the console.
4. firstFunction() is pop off the stack.
5. The execution order then move to secondFunction().
6. secondFunction() returns and print “The end from secondFunction” to the console.
7. secondFunction() is pop off the stack, clearing the memory.


### What causes a stack overflow?
> ***A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.***


------------------------------------------------------------------------------------------------------------------


# Types of error messages
![vsddsvs](https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2019/08/JavaScript-Errors.jpg)

### The first thing that indicates you that something is wrong with your code is the (in)famous error message that the one we saw just moments ago, it usually appears on your console (being developer tools of the browser, terminal or whatever else you are using).


### For those already used to programming, reading an error message is like second nature, for everybody else, is something you learn either you like it or not so might as well talk a bit about each of them.
Reference errors 

* This is as simple as when you try to use a variable that is not yet declared you get this type os errors `console.log(foo) //` Uncaught ReferenceError: `foo is not defined`


* This is also a common thing when using const and let, they are hoisted like var and function but there is a time between the hoisting and being declared so when you try to access them a reference error occurs, the fact that this happens to let and const is called Temporal Dead Zone (TDZ).
`foo = 'Hello' //` Uncaught ReferenceError: `foo is not defined`
```
let foo
Whatever you are using (var, let or const) the fix is as simple has declaring the variable before any declaration is made.
let foo;
foo = 'Hello'
Syntax errors
```
### I know it’s in the name of the errors, but like it says itself, this occurs when you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse!!.


`JSON.parse( {'foo': 'bar'} ) //` Uncaught SyntaxError: `Unexpected token o in JSON at position 1`

* This can be solved by just fixing the syntax, in this case the object should be a JSON.
`JSON.parse('{"foo":"bar"}')`

### Some syntax errors like sending a trailing comma when calling a function are handled without error by most recent browsers, but older ones you have to be careful.

1. Range errors
#### Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.
```
var foo= []
foo.length = foo.length -1 // Uncaught RangeError: Invalid array length
An array for instance cannot have a negative length, why would you mess with the array length? Some people use it to set an array to empty, something of the likes of:
var foo = [0, 0]
foo.length = foo.length - 2 // (or foo.length - foo.length)
foo // would log [] instead of [0, 0]
```

### I prefer not to mutate my variables whenever possible (making them constants and not variables) but this is a method that is available and now you know it.

2. Type errors
* `Like the name indicates`, this types of errors show up when the types `(number, string and so on)` you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.
```
var foo = {}
foo.bar // undefined
foo.bar.baz // Uncaught TypeError: Cannot read property 'baz' of undefined
This is probably the most frequent error in JS, trying to access a property/method thinking that bar is of the type object when in reality, since it hasn’t been declared yet, it’s undefined which doesn’t have any baz available.
The fix is simple, just make sure that bar exists before trying to access it, either by creating bar or by checking for undefined.
var foo = { bar: {} }
foo.bar.baz // undefined but you avoid the error
```
#### or
```
var foo = {}
if (typeof foo.bar !== 'undefined') {
  foo.bar.baz // this will never be executed while bar does not exist
}
```

* There are also warnings, for instance telling you about a deprecated method, which can be found more frequently in firefox developer tools.


# List of errors
 > (the type of error) and message (a more detailed human-readable error message). Together, these two properties provide a starting point toward understanding and resolving the error.

1. Error: Permission denied to access property "x"
2. InternalError: too much recursion
3. RangeError: argument is not a valid code point
4. RangeError: invalid array length
5. RangeError: invalid date
6. RangeError: precision is out of range
7. RangeError: radix must be an integer
8. RangeError: repeat count must be less than infinity
9. RangeError: repeat count must be non-negative
10. ReferenceError: "x" is not defined
#### And many others you can check it [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors)


##### References
1. [developer.mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors)

2. [codeburst.io](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c)
3. [freecodecamp](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/)