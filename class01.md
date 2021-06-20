# Class 01

## **Component-based architecture**

![Component-based architecture](https://files.speakerdeck.com/presentations/a222ec40e0010130dca416e8f5cd5baf/slide_1.jpg)

> # *Definitions* 

### *What is a component?*

1.  A component is a modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface.

2. A component is a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities. It has an obviously defined interface and conforms to a recommended behavior common to all components within an architecture.

### ` So a software component can be defined as a unit of composition with a contractually specified interface and explicit context dependencies only. That is, a software component can be deployed independently and is subject to composition by third parties.`

> Component-based architecture focuses on the decomposition of the design into individual functional or logical components that represent well-defined communication interfaces containing methods.


### Component-oriented software design has many advantges 

Num|Adv                                                                           
-|-
1|Reduced time in market and the development cost by reusing existing components.
2|Increased reliability with the reuse of the existing components.


### A component can have three different views 

Num|Type|Def
-|-|-
1|Object-oriented view  |    A component is viewed as a set of one or more cooperating classes.(Implementation and analysis)
2|Conventional view|     It is viewed as a functional element or a module of a program that integrates the processing logic, the     internal data structures that are required to implement the processing logic and an interface that enables the component to be invoked and data to be passed to it.
3|Process-related view|   instead of creating each component from scratch, the system is building from existing components maintained in a library. (useful whem UI, JIT AND EJB)


#### UI : A user interface (UI) component includes grids, buttons referred as controls, and utility components expose a specific subset of functions used in other components.

#### JIT: Must be activated using the just-in-time 

#### EJB : Many components are invisible which are distributed in enterprise business applications and internet web applications such as Enterprise JavaBean (EJB), .NET components, and CORBA components.

> Characteristics of Components
* Independent : Components are designed to have minimal dependencies on other components.
* Encapsulated:A component depicts the interfaces, which allow the caller to use its functionality, and do not expose details of the internal processes or any internal variables or state.
* Extensible:  A component can be extended from existing components to provide new behavior.
* Not context specific: Components are designed to operate in different environments and contexts.
* Replaceable: Components may be freely substituted with other similar components.
* Reusability: Components are usually designed to be reused in different situations in different applications.


### What are the advantages of using component based architecture?

> A component-level design can be represented by using some intermediary representation (e.g. graphical, tabular, or text-based) that can be translated into source code. The design of data structures, interfaces, and algorithms should conform to well-established guidelines to help us avoid the introduction of errors.

1. The software system is decomposed into reusable, cohesive, and encapsulated component units.

2. Each component has its own interface that specifies required ports and provided ports; each component hides its detailed implementation.

3. A component should be extended without the need to make internal code or design modifications to the existing parts of the component.

4. Depend on abstractions component do not depend on other concrete components, which increase difficulty in expendability.

5. Connectors connected components, specifying and ruling the interaction among components. The interaction type is specified by the interfaces of the components.

6. Components interaction can take the form of method invocations, asynchronous invocations, broadcasting, message driven interactions, data stream communications, and other protocol specific interactions.

7. For a server class, specialized interfaces should be created to serve major categories of clients. Only those operations that are relevant to a particular category of clients should be specified in the interface.

8. A component can extend to other components and still offer its own extension points. It is the concept of plug-in based architecture. This allows a plugin to offer another plugin API.




------------------------------------------------------------------------------------------------------------------------------------



## **Props**
![Props](https://www.techdiagonal.com/wp-content/uploads/2019/09/react-props-blog-image-design.jpg)


## What is Props?


 #### React is a component-based library which divides the UI into little reusable pieces. In some cases, those components need to communicate (send data to each other) and the way to pass data between components is by using props.
 

 `“Props” is a special keyword in React, which stands for properties and is being used for passing data from one component to another.`

### Using Props in React
- Firstly, define an attribute and its value(data)
   - Then pass it to child component(s) by using Props
      - Finally, render the Props Data



## What is the flow of props?
> Props is a special keyword in React, which stands for properties and is being used for passing data from one component to another.

*But the important part here is that data with props are being passed in a uni-directional flow. (one way from parent to child)
Furthermore, props data is read-only, which means that data coming from the parent should not be changed by child components.*

**Recap**:
- [x] Props stand for properties and is a special keyword in React
- [x] Props are being passed to components like function arguments
- [x] Props can only be passed to components in one-way (parent to child)
- [x] Props data is immutable (read-only)


*The informations is from [INTEXT](https://itnext.io/what-is-props-and-how-to-use-it-in-react-da307f500da0)* 





-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*From Bookmark/Skim*


## **Rendering Elements**

### Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.



> ### Rendering an Element into the DOM
- Let’s say there is a <div> somewhere in your HTML file:

`<div id="root"></div>`
*We call this a “root” DOM node because everything inside it will be managed by React DOM.*

- Applications built with just React usually have a single root DOM node. If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.

***To render a React element into a root DOM node, pass both to `ReactDOM.render():`***


> ### Updating the Rendered Element
- React elements are immutable. Once you create an element, `you can’t change its children or attributes`, An element is like a single frame in a movie: it represents the UI at a certain point in time.

***The only way to update the UI is to create a new element, and pass it to `ReactDOM.render().`***


> ### React Only Updates What’s Necessary
***React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.***


#### Even though we create an element describing the whole UI tree on every tick, only the text node whose contents have changed gets updated by React DOM.
