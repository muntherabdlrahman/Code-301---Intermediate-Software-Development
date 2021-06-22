# Lists and Keys
![hjh](https://i.ytimg.com/vi/0sasRxl35_8/maxresdefault.jpg)


> Given the code below, we use the map() function to take an array of numbers and double their values. We assign the new array returned by map() to the variable doubled and log it:
````
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);
This code logs [2, 4, 6, 8, 10] to the console.
````
In React, transforming arrays into lists of elements is nearly identical.

### Rendering Multiple Components
> **You can build collections of elements and include them in JSX using curly braces `{}`.**

> we loop through the numbers array using the JavaScript map() function. We return a <li> element for each item. Finally, we assign the resulting array of elements to listItems:
`````
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);
`````
> **We include the entire listItems array inside a <ul> element, and render it to the DOM:**
```
ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
```

> **This code displays a bullet list of numbers between 1 and 5.**

### Basic List Component
> **Usually you would render lists inside a component.**
> We can refactor the previous example into a component that accepts an array of numbers and outputs a list of elements.



#### When you run this code, you’ll be given a warning that a key should be provided for list items. A “key” is a special string attribute you need to include when creating lists of elements. We’ll discuss why it’s important in the next section.

> **Let’s assign a key to our list items inside `numbers.map()` and fix the missing key issue.**


# Keys
> ***Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity:***
````
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>
    {number}
  </li>
);
````



 - We don’t recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.
 *** Check out Robin Pokorny’s article for an in-depth explanation on the negative impacts of using an index as a key. If you choose not to assign an explicit key to list items then React will default to using indexes as keys.***


### Extracting Components with Keys
> ***Keys only make sense in the context of the surrounding array.***

> For example, if you extract a ListItem component, you should keep the key on the `<ListItem />` elements in the array rather than on the `<li>` element in the ListItem itself.




#### Note Sometimes this results in clearer code, but this style can also be abused. Like in JavaScript, it is up to you to decide whether it is worth extracting a variable for readability. Keep in mind that if the map() body is too nested,

#### The informations is from [reactjs.org](https://reactjs.org/docs/lists-and-keys.html)


------------------------------------------------------------------------------------------------------------------------------------




# What is the spread operator?
> ***InJavaScript, spread syntax refers to the use of an ellipsis of three dots (…) to expand an iterable object into the list of arguments.***
 
#### “When ...arr is used in the function call, it ‘expands’ an iterable object arr into the list of arguments.” — JavaScript.info

#### The spread operator was added to JavaScript in ES6 (ES2015), just like the rest parameters, which have the same syntax: three magic dots ….




## What is ... used for?
> **“Spread operator to the rescue! It looks similar to rest parameters, also using ..., but does quite the opposite.” — JavaScript.info**
>Take trying to find the largest number in an array with Math.max():




## What else can … do?
> **The … spread operator is useful for many different routine tasks in JavaScript, including the following:**


Num|Operator
-|-
1|Copying an array
2|Concatenating or combining arrays
3|Using Math functions
4|Using an array as arguments
5|Adding an item to a list
6|Adding to state in React
7|Combining objects
8|Converting NodeList to an array