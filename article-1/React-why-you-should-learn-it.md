# React, why you should learn it.

**Table of contents**
1. [Introduction](#introduction)
2. [React](#react)
3. [Components and Props](#components-and-props)
4. [State and Lifecycle](#state-and-lifecycle)
5. [Redux](#redux)
6. [What is Redux?](#what-is-redux?)
7. [When to use Redux?](#when-to-use-redux?)
8. [Summary](#summary)
9. [Sources](#sources)
# React, why you should learn it.
## Introduction
Frameworks are a much sought after skill as a web developer nowadays. There are many reasons why. The fact that they are based on components, have a strong community and have many third party libraries are some of those reasons. But the biggest reason is that keeping the UI in sync with the state is hard. In this article I want to show you how react makes this easier for you and why this should matter to you.
React
In the last six month I have worked at a company that has a big and complex application called the stageplayer [link]. In the stageplayer we used react and redux so that we had reusable pieces of code called components, that had a state 

[img] stageplayer
	

## Components and Props
Components let you split the UI into reusable pieces, and think about each piece in isolation. Components are like JavaScript functions. they accept inputs called props. 
```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```
## State and Lifecycle
State is basically the state of the app at that current time and moment. By using states you can for example toggle things in your design or save the input data. In your state you can define infite property's. Whenever one of the property's change in the state, React will re render the components or ui elements that rely on this property.
## Redux
## What is Redux?
## When to use Redux?
Class based components
Class based compenents are usually used in React as containers where you hold your smaller components (functinoal components). This Class based component has the ability to hold states. These states can be passed on as props to the child components. Often you also hold your functions in an class based components.

A Class based component is also the only component which can use lifecycle hooks.

You can make lots of Class based components, but when you have a big applications it becomes unclear real fast where you hold certain states. So it is smart to make Class components sparingly and wisely.

Functional Components
Most of your app consists of Functional components. These components are often used to for displaying purposes. Functional components often have props that were passed on from a Class based component and based on these props certain ui elements will show or even the whole component.

NOTE: because of React hooks you can even hold states in your functional components!!! So you can build an entire app from only functional components


## Summary
## Sources
- https://medium.com/dailyjs/the-deepest-reason-why-modern-javascript-frameworks-exist-933b86ebc445
- https://reactjs.org/docs/getting-started.html
- https://redux.js.org/tutorials/essentials/part-1-overview-concepts
- https://www.robinwieruch.de/react-function-component#react-arrow-function-component

