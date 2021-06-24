# React Doc

![dfsf](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQyoY20BQzn6u3UTnzEqikpjORmtN313qOM3w&usqp=CAU)

### **How would you break a mock into a component heirarchy?**
> *first thing you’ll want to do is to draw boxes around every component in the mock and give them all names. Use the same techniques for deciding if you should create a new function or object.*

### What is the single responsibility principle and how does it apply to components?
> *single responsibility principle technique, that is, a component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.*


### What does it mean to build a ‘static’ version of your application?
>*Build a version that takes your data model and renders the UI but has no interactivity.*

### Once you have a static application, what do you need to add?
> *We need to Identify The Minimal Representation Of UI State o do is to draw boxes around every component (and subcomponent) in the mock and give them all names. If you’re working with a designer, they may have already done this, so go talk to them! Their Photoshop layer names may end up being the names of your React components!*

### What are the three questions you can ask to determine if something is state?
> *Is it passed in from a parent via props? If so, it probably isn’t state.
Does it remain unchanged over time? If so, it probably isn’t state.*

### Can you compute it based on any other state or props in your component? If so, it isn’t state.
### How can you identify where state needs to live?
> *Identify every component that renders something based on that state.*



#### Resorces [reactjs.org](https://reactjs.org/docs/thinking-in-react.html)



#### the form components deep in the hierarchy need to update the state in FilterableProductTable.

### `React makes this data flow explicit to help you understand how your program works, but it does require a little more typing than traditional two-way data binding.`

### `If you try to type or check the box in the current version of the example, you’ll see that React ignores your input. This is intentional, as we’ve set the value prop of the input to always be equal to the state passed in from FilterableProductTable.`

- Let’s think about what we want to happen. We want to make sure that whenever the user changes the form, we update the state to reflect the user input. Since components should only update their own state, 
- FilterableProductTable will pass callbacks to SearchBar that will fire whenever the state should be updated. We can use the onChange event on the inputs to be notified of it. The callbacks passed by FilterableProductTable will call `setState()`, and the app will be updated.