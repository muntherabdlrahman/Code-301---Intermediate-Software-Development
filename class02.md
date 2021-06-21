# React: Component Lifecycle Events 

![React life](https://miro.medium.com/max/2800/0*pqn5ljaOw4kWrUdF) 

## `What are component lifecycle events?`
***React lets you define components as classes or functions. The methods that you are able to use on these are called lifecycle events. These methods can be called during the lifecycle of a component, and they allow you to update the UI and application states.***

![explanitions](https://miro.medium.com/max/2800/0*0saPKFiTUk6W3FYp)

1. **Mounting**
***When an instance of a component is being created and inserted into the DOM it occurs during the mounting phase. Constructor, static getDerivedStateFromProps, render, componentDidMount, and UNSAFE_componentWillMount all occur in this order during mounting.***
2. **Updating**
***Anytime a component is updated or state changes then it is rerendered. These lifecycle events happen during updating in this order.***


- static--getDerivedStateFromProps 
- shouldComponentUpdate
- render
- getSnapshotBeforeUpdate 
- componentDidUpdate 
- UNSAFE_componentWillUpdate 
- UNSAFE_componentWillReceiveProps


1. **Unmounting**
> The final phase of the lifecycle if called when a component is being removed from the DOM. componentWillUnmount is the only lifecycle event during this phase.

2. **constructor()**
> The constructor for a React component is called before it is mounted.If the component is a subclass you should call `super(props)`, or the props will be undefined. constructors can be used to assign state using this.state or to bind event handle methods to an instance. 


3. **static getDerivedStateFromProps()**
> This method exists for rare cases where the state relies on changes in props over time.

4. **render()**
> *Render* is the only required method in a class component. It will examine `this.props` and `this.state` when called. The render function should not modify the component state because it would cause a lot of bugs by changing the state every time it rerenders. I also should not directly interact with the browser. render will not be invoked if `shouldComponentUpdate()` returns `false`. 


5. **componentDidMount()**
> This method is invoked *immediately* after a component is *mounted*. If you need to load anything using a network request or initialize the DOM, it should go here. This method is a good place to set up any subscriptions. If you do that, don’t forget to unsubscribe in `componentWillUnmount()`.
`setState()` can be called here, but it should be used sparingly, because it will cause a rerender, which can lead to perfomance issues.


6. **shouldComponentUpdate()**
> The default behavior in react is to rerender after every state change. Setting `shouldComponentUpdate()` to false allows you to prevent this from happening. This is in order to optimize performance. If you want to use this method, it may be better to use PureComponent instead, which performs a shallow comparison of props and state. 

### If you do decide to use this method, be sure to check the previous props and state with the current props and state. If `shouldComponentUpdate()` returns `false`, then `UNSAFE_componentWillUpdate()`, `render()`, and `componentDidUpdate()` will not be invoked.

7. **getSnapshotBeforeUpdate()**
> This is another rarely used method that allows you to capture a picture of the DOM to check it before actually changing anything on the DOM.

8. **componentDidUpdate()**
> This method is useful for performing network requests after a change has occurred.


9. **componentWillUnmount()**
> This method allows you to clean up the DOM and netwrok requests/ subscriptions.


### UNSAFE Lifecycle Events
**UNSAFE_componentWillMount()**
**UNSAFE_componentWillUpdate()**
**UNSAFE_componentWillReceiveProps()**

#### These events have lead to a lot of bugs and unintended side effects, so in React 17 these will no longer be able to be used without the UNSAFE tag in front of them. Instead of componentWillMount use ComponentDidMount.


## Here is a handy chart to help you keep track of the lifecycle events


![unsafe](https://miro.medium.com/max/778/1*4y9V5936WdJKaIeVPFEa3w.png)
 
*References* [Joshua Blankenship](https://medium.com/@joshuablankenshipnola/react-component-lifecycle-events-cb77e670a093)




------------------------------------------------------------------------------------------------------------------------------------




# React State Vs Props

1. What types of things can you pass in the props?
### Props
>  like arguments to a function when you create a component inside of react and you wantto render it you're going to pass it the props that you want to give to it for example. 

> For information is static and not going to change for example inside the component you never need to update the title of that display section then you want to use props because props are for things that are going to be passed down from the parent and don't change inside the component but with the counter like I mentioned we're updating that in the component so we need to use.

2. What is the big difference between props and state?

> Big difference between state and props state is handled in the component and you can update it inside the component while props are handled outside the component and must be updated outside of the component another

3. When do we re-render our application?

> When you change the state inside of your application it's going to re-render that section of your application but props you can't actually change them you need to change them outside the component like we talked about most likely it's going to be state stored somewhere else in your application that's being passed down as props going back to our subtitle entitled component most likely this




4. What are some examples of things that we could store in state?

> You don't want to store JSX in the state. Instead, store the model data for it, and loop through your data to print your elements And inside your render method, you can use these data about the tabs you have stored in your state to render your custom component.
