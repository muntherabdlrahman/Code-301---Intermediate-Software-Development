# Forms

![forms](https://www.techfry.com/images/articles/html/html-forms.jpg)


***HTML form elements work a bit differently from other DOM elements in React, because form elements naturally keep some internal state.***


#### If you want this behavior in React, it just works. But in most cases, it’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form. The standard way to achieve this is with a technique called “controlled components”.

### Controlled Components
>**In HTML, form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with `setState()`.**


### what is “controlled component”?
> #### We can combine the two by making the React state be the “single source of truth”. Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”.


***Since the value attribute is set on our form element, the displayed value will always be this.state.value, making the React state the source of truth. Since handleChange runs on every keystroke to update the React state, the displayed value will update as the user types.***

***With a controlled component, the input’s value is always driven by the React state. While this means you have to type a bit more code, you can now pass the value to other UI elements too, or reset it from other event handlers.***

### The textarea Tag

> In HTML, a `<textarea>` element defines its text by its children:
``````````
`<textarea>`
  Hello there, this is some text in a text area
`</textarea>`
 ``````````
``````
In React, a <textarea> uses a value attribute instead
``````

### The select Tag
##### In HTML, `<select>` creates a drop-down list
> ***Note that the Coconut option is initially selected, because of the selected attribute. React, instead of using this selected attribute, uses a value attribute on the root select tag. This is more convenient in a controlled component because you only need to update it in one place***

> ***Overall, this makes it so that `<input type="text">`, `<textarea>`, and `<select>` all work very similarly - they all accept a value attribute that you can use to implement a controlled component.***


> **Note : You can pass an array into the value attribute, allowing you to select multiple options in a select tag:**
``````
<select multiple={true} value={['B', 'C']}>
``````


### The file input Tag
> In HTML, an `<input type="file">` lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the File API.

`<input type="file" />`
> Because its value is read-only, it is an uncontrolled component in React. It is discussed together with other uncontrolled components later in the documentation.


### Handling Multiple Inputs
> When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.



### Controlled Input Null Value
> Specifying the value `prop` on a controlled component prevents the user from changing the input unless you desire so. If you’ve specified a value but the input is still editable, you may have accidentally set value to undefined or null.


### Alternatives to Controlled Components
***It can sometimes be tedious to use controlled components, because you need to write an event handler for every way your data can change and pipe all of the input state through a React component. This can become particularly annoying when you are converting a preexisting codebase to React, or integrating a React application with a non-React library. In these situations, you might want to check out uncontrolled components, an alternative technique for implementing input forms.***

### Fully-Fledged Solutions
***If you’re looking for a complete solution including validation, keeping track of the visited fields, and handling form submission, Formik is one of the popular choices. However, it is built on the same principles of controlled components and managing state — so don’t neglect to learn them.***

##### Informaions is from [reactjs.org](https://reactjs.org/docs/forms.html)



-----------------------------------------------------------------------------------------------------------------------------------



# The Ternary Operator



#### The Ternary Operator
> ***This article is meant for users of PHP, however, it may be a good resource for other programming languages as well.***

### What is the Ternary Operator?
> **The ternary operator is an operator that takes three arguments. The first argument is a comparison argument, the second is the result upon a true comparison, and the third is the result upon a false comparison. If it helps you can think of the operator as shortened way of writing an if-else statement. It is often used as a way to assign variables based on the result of an comparison. When used correctly it can help increase the readability and reduce the amount of lines in your code.**

### How Do I Use the Ternary Operator?
> **The ternary operator is really very simple to use. The ternary operator, as mentioned above, consists of three parts, the condition, the result if true, and the result if false.**



### When Do I Use the Ternary Operator?
> **Use the ternary operator to simplify your if-else statements that are used to assign values to variables. The ternary operator is commonly used when assigning post data or validating forms. For example if we were programming a comment form and wanted to ensure that the user entered their email address then we could write something like the following.**


### Rewrite the following statement using a ternary statement:
``````````
  if(x===y){
 console.log(true);
  } else {
 console.log(false);
  }
``````````
#### answer
```
//if-else
   if($x===y')
   {
      $ console.log(true);

   }
   else
   {
      $ console.log(false);

   }
```