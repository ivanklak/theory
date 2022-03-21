# React

## Main features

1. **Components** - easy to understand
2. **Virtual DOM** - is a programming concept where an`virtual` representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM. This process is called `reconciliation`.

React looking for differences and **replaces the virtual element of the object with a new one**, and then creates a new real DOM-element. 

 - You tell React what state you want the UI to be in, and it makes sure the DOM matches that state.
 - React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

3. **Unidirectional Data Flow**

In React this means that:

- state is passed to the view and to child components
- actions are triggered by the view
- actions can update the state
- the state change is passed to the view and to child components

4. **JSX** - syntax for describing the interface structure. 
5. **isomorphism** -  this means that the server renders the initial HTML for the client using React components. 

React is executed on the client side and rendered on the server side. 

## How React works?

- Components written in `JSX` are converted to pure JS using `Babel` (transpiler)
- after that, the React function `React.createElement` converts them into a VDOM tree. 
- And `Preacts VDOM` algorithm creates a real DOM from VDOM. 

## The difference between props and state 

- `props` - this is the input data that is passed to the component from the outside. 
- `state` - it stores data that is created in the component and is completely dependent on the component. The state can be passed to child components using props. 

## JSX

The logic of rendering is related to the logic of the user interface. 

Instead of artificially **separating technologies** by putting markup and logic in separate files, **React separates tasks using components that contain both markup and logic.**

`React.createElement` - create and return new React-element. Each JSX element - `syntax sugar` for React.createElement. 


## Controlled Conponent && Uncontrolled Component 

**Controlled** - there is `state` we are monitoring (setState or useState)

**Uncontrolled** - there is `state` but we dont process it and do not update it. 

## Class Components

You can use an `ES6 class` to define a component. 

1. local state with constuctor() and render() methods. 
- `render()` is not user callable. **It is part of the React component lifecycle**. Generally, it gets called by React at various app stages **when the React component instantiates for the first time, or when there is a new update to the component state**. Render does not take any arguments and returns a `JSX.Element` which contains the view hierarchy of the current component. 

- `constructor()` - is a method that’s automatically called during the creation of an object from a class. **It can handle your initial setup stuff like defaulting some properties of the object**. In React it can be used **to bind event handlers to the component and/or initializing the local state of the component**. The `constructor()` method is fired before the component is mounted. 

**Constructor rules:**
- Call `super(props)` before using `this.props` - because of the nature of the constructor `this.props` object is not available. When you call the `super()` method, it calls the constructor of the parent class. 
- Never call  `setState()` inside `constructor()` - you need to set the initial state directly. 
- Avoid assigning values from `this.props` to `this.state`.

2. lyfe cycle methods


