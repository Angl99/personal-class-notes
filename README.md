
## React Notes

# JSX
- JSX is a syntax extension for JavaScript used with React. JSX allows you to write HTML elements and components in a syntax that is similar to HTML, directly within your JavaScript code and make it easier to create and manipulate html elements. 

EX: 
```js
    const element = <h1>Hello, JSX!</h1>;
```

# Props
- Props are properties used to pass data from one component to another. Particuarly from parent to child components. Props are immutable and are passed to components via HTML attributes.

EX: 
```js
    // Parent Component (Usually seen in App.js)
    const ParentComponent = () => {
    return <ChildComponent name='John' age='25' />;
    };

    // Child Component (randomComponent.js)
    const ChildComponent = (props) => {
    return (
        <div>
        <p>Name: {props.name}</p>
        <p>Age: {props.age}</p>
        </div>
    );
    };
```
# State
- State is an object that holds information that is used by a component. 
- State is mutable and is managed within the component which can be updated over time in response to users actions or other events. 
- One important thing to note about state is that when we call the useState hook, it returns an array with two elements. The first element is the current value of the state, and the second element is a function that can be used to update the state. 
- You can think of state as the internal memory of a component. It allows a component to keep track of information that might change during its lifecycle.


Ex: 
```js
import React, { useState } from 'react';


function Counter(){
    const [count, setCount] = useState(0)
    return (
        <div>
            <h2>{count}</h2>
            <button onClick={() => setCount(count + 1)}>+1</button>
        </div>
    )
}


export default Counter;
```

# Class Components vs Functional Components
- In React, there are two primary ways to create components: class components and functional components 
- As of React 16.8, functional components are more commonly used due to the introduction of Hooks
    - Which allow functional components to manage state and perform side effects

```js
// Class Component
import React from "react";

class ClassGreeting extends React.Component {
    render() {
        return (
        <div>
            <h1>Greetings, {this.props.name}</h1>
        </div>
        )
    }
}

export default ClassGreeting;
```
- Importing is React is required because class components extend(indicates that a class is inherited from another class) the React.Component class

```js
// Functional Component
import React from "react";

const FunctionalGreeting = (props) => {
  return (
    <div>
      <h1>Greetings, {props.name}</h1>
    </div>
  );
};

export default FunctionalGreeting;
```
- Syntax: Functional components are defined as JavaScript functions. They take props as an argument and return JSX.
- Hooks: Functional components can use React Hooks, such as useState and useEffect

# Use Effect
```js
import React, { useState, useEffect } from "react";

function TitleChanger() {
    const [name, setName] = useState('John');

    useEffect(()=>{
        document.title = name; 
    },[name]);
    return (
        <div>
            <h1>Hello: {name}</h1>
            <input type="text" value={name} onChange={(event) => setName(event.target.value)} />
        </div>
    )
}


export default TitleChanger;
```
- useEffect is a hook in React that allows you to perform side effects in functional components
- It's used to manage side effects in React components, such as data fetching and DOM manipulation
- It takes two arguments: a function (the effect itself) and an optional array of dependencies. The function contains the code to execute the side effect, and the array of dependencies specifies when the effect should run.