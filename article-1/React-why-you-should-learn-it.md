# React, why you should learn it.

**Table of contents**
1. [Introduction](#introduction)
2. [React](#react)
3. [Components and Props](#components-and-props)
4. [State and Lifecycle](#state-and-lifecycle)
5. [Redux](#redux)
6. [What is Redux](#what-is-redux)
7. [When to use Redux](#when-to-use-redux)
8. [Summary](#summary)
9. [Sources](#sources)
# React, why you should learn it.
## Introduction
Frameworks are a much sought after skill as a web developer nowadays. There are many reasons why. The fact that they are based on components, have a strong community and have many third party libraries are some of those reasons. But the biggest reason is that keeping the UI in sync with the state is hard. In this article I want to show you how react makes this easier for you and why this should matter to you.
## React
In the last six month I have worked at a company that has a big and complex application called the [stageplayer](https://stageplayer.nl/nl/). In the stageplayer we used react and redux so that we had reusable pieces of code called components, that had a state 

![Screenshot of the stageplayer](https://github.com/JimvandeVen/weekly-nerd-2020/blob/master/article-1/chrome_d1aGaSLaEg.png)
	

## Components and Props
Components let you split the UI into reusable pieces, and think about each piece in isolation. Components are like JavaScript functions. They accept inputs called props. For example, this code renders "Hello, Jim":
```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Jim" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```

This piece of code is nice when you want to render something on the page dynamically. But it still needs to be manually ‘told’ to change. What if you have, for example, a clock ticking on your website. You would want it to update the DOM automatically. But with React components there is one golden rule: 
**All React components must act like pure functions with respect to their props.** 
Meaning that React components may never modify its own props. This is where state and lifecycle comes in.
## State and Lifecycle
State holds the current state of the app. With state you can ‘save’ input data, UI status (hidden, dark mode, etc.) and many more properties. Then whenever one or more properties change in the state, React will re-render **only** the components that rely upon those properties.

Lets look at a ticking clock to make this more clear.

```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  componentDidMount() {
    this.timerID = setInterval( // iuswahedfiuhsewdf
      () => this.tick(),
      1000
    );
  }

  componentWillUnmount() {
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

## Redux
## What is Redux
## When to use Redux
## Summary
## Sources
- https://medium.com/dailyjs/the-deepest-reason-why-modern-javascript-frameworks-exist-933b86ebc445
- https://reactjs.org/docs/getting-started.html
- https://redux.js.org/tutorials/essentials/part-1-overview-concepts
- https://www.robinwieruch.de/react-function-component#react-arrow-function-component

