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

**React without JSX** - it's possible. JSX - it's just `syntactic sugar` for calling the `React.createElement` function. Therefore, you can do everything on a regular js. 

**JSX without React** - it's possible. Most transpilers allow you to choose your own `JSX pragma` (A function that will instead of `React.createElement`). 

## Controlled Conponent && Uncontrolled Component 

**Controlled** - there is `state` we are monitoring (setState or useState)

**Uncontrolled** - there is `state` but we dont process it and do not update it. 

## Class Components

You can use an `ES6 class` to define a component. 

1. local state with constuctor() and render() methods. 
- `render()` is not user callable. **It is part of the React component lifecycle**. Generally, it gets called by React at various app stages **when the React component instantiates for the first time, or when there is a new update to the component state**. Render does not take any arguments and returns a `JSX.Element` which contains the view hierarchy of the current component. 

> to update state: `this.setState()` - it runs rerender propcess. 

- `constructor()` - is a method that’s automatically called during the creation of an object from a class. **It can handle your initial setup stuff like defaulting some properties of the object**. In React it can be used **to bind event handlers to the component and/or initializing the local state of the component**. The `constructor()` method is fired before the component is mounted. 

**Constructor rules:**
- Call `super(props)` before using `this.props` - because of the nature of the constructor `this.props` object is not available. When you call the `super()` method, it calls the constructor of the parent class. 
- Never call  `setState()` inside `constructor()` - you need to set the initial state directly. 
- Avoid assigning values from `this.props` to `this.state`.

2. **lyfe cycle methods** - can be defined as the series of methods that are involked in different stages of the components existence. 

**Mounting - when a Component is rendered to the DOM for the first time.**

Process: `componentWillMount()` -> `constructor()` [setting the initial state] -> `render()` -> `componentDidMount()`

The `componentWillMount()` method runs before the component render.  

The `componentDidMount()` method runs after the component output has been rendered to the DOM. 

**Updating - when we have updated state**

Process: `compnentWillReceiveProps` [only for props] -> `shouldComponentUpdate()` [old method] -> `componentWillUpdate` -> `rendder` -> `componentDidUpdate()`

**Unmount - component will die**

`componentWillUnmount()` - involke somethig when Component died. For example, timers using: `clearInreval()`, because timers happen in browser. 

**Errors**

`componentDidCatch()` - this method is called when an error occurs in the **lifecycle method** or in the **constructor** of a child component. 


**-----**

1. if we have REDUX in our project, `local state` is useless. 
2. Using the class component, React creates an object in memory, which takes up extra space in memory. 

## Functional Components

- it is like a function, that return JSX. 
- use Hooks for lifecycle methods and store local state. 

## Hooks

**A `Hook` is a special function that lets you “hook into” React features.** 

When React sees Hooks, it remembers which function the results of the Hooks call are associated with. And store it all somewhere on the React side without clogging up memory.

For example, `useState` is a Hook that lets you add React state to function components.

**useState**

`useState` - takes the initial value and returns an array, in which **the first element** is a value, and **the second** is a function that sets this value. 

```js
const [count, setCount] = useState(0); // [count, setCount] - destructurization.
```

**useEffect**

The Effect Hook lets you perform side effects in function components. 

By using this Hook, you tell React that your component needs to do something after render. React will remember the function you passed (we’ll refer to it as our “effect”), and call it later after performing the DOM updates. We could also perform data fetching or call some other imperative API.

`useEffect` - launches some function after everything is rendered. It runs after each render. But you can tell React to skip applying an effect if certain values haven’t changed between re-renders. To do so, pass an **array as an optional second argument**. 

React will compare [props.status] from the previous render and [props.status] from the next render. If these parameters are different, `useEffect` will start. 

```js
let [status, setStatus] = useState("");

useEffect(() => {
 setStatus(props.status);
}, [props.status]);
```

`useEffect` Hook combined `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

 `componentWillUnmount` - to do so, we should return function from useEffect:
 
 ```js
 useEffect(() => {
 // some code
  return () => {
       ChatAPI.unsubscribeFromFriendStatus();
  };
}, []);
 ```
 
 **useContext**
  
```js
const value = useContext(MyContext);
```
 
Accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context. 
 
When the nearest `<MyContext.Provider>` above the component updates, this Hook will trigger a rerender with the latest context value passed to that `MyContext` provider. 

A component calling `useContext` will always re-render when the context value changes.

**useMemo**

```js
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

`useMemo` - Returns a memoized value - pass a “create” function and an array of dependencies. `useMemo` will only **recompute the memoized value** when one of the dependencies has changed. This optimization helps to avoid expensive calculations on every render.

You may rely on useMemo as a performance optimization. 

**useCallback**

```js
const memoizedCallback = useCallback( () => { doSomething(a, b) }, [a, b]);
```

`useCallback` - Returns a memoized callback - Pass an inline callback and an array of dependencies. `useCallback` will return a memoized version of the **callback that only changes if one of the dependencies has changed**. This is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders

**useRef**

```js
const refContainer = useRef(initialValue);
```

`useRef` returns a **mutable ref object** whose `.current` property is initialized to the passed argument (initialValue). The returned object will persist for the full lifetime of the component.

```js
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

`ref` - HTML-element attribute - used to get a reference to a DOM node or React component.

For example: to make `focus()` on the element, interact with text or as a second parameter in React.createPortal. 








