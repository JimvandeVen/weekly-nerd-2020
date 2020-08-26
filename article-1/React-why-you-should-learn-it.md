# React, why you should learn it.

**Table of contents**
1. [Introduction](#introduction)
2. [React](#react)
3. [Components and Props](#components-and-props)
4. [State and Lifecycle](#state-and-lifecycle)
5. [Redux](#redux)
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
    this.timerID = setInterval(
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
This piece of code may seem intimidating at first. Let's dissect it one line at a time.

1. When `<Clock />` is passed to `ReactDOM.render()`, React calls the constructor of the Clock component. At first Clock needs to display the current time, so it initializes `this.state` with an object including the current time.
2. React updates the DOM using the `render()` method, displaying the clock.
3. When the Clock output is inserted in the DOM, React calls the `componentDidMount()` lifecycle method. There the browser will set a timer to call the `tick()` method every 1000 milliseconds.
4. Each time the `tick()` method is called the state gets updated by calling `setState()` with an object containing the current time. Because we are using the `setState()` call, React knows the state has changed and calls the `render()` method again. Now `this.state.date` has a different value and React will update the DOM with this value.

I hope you can see why this is really neat. Even for small projects it makes the hassle of keeping the UI up to date with the current state of the application much less cumbersome. This is especially so for big projects, where there are many more components and many more state properties that will change. By using React components you can automate a lot of the UI updates by letting the components be dependent on the state.

## Summary
We have taken a quick look at what React components are and what it can do for you. What state and lifecycle mean. How to write proper components that automatically update the DOM when the state changes and how this can help you write concise, reusable and independent pieces of code.  

And if that is not enough incentive to start learning React, take a look at all the BIG companies that are using the framework: Facebook, AirBnB, Uber, Stackoverflow, BBC, PayPal and many more…  

Think about the job opportunities! 

## Sources
- Gimeno, A. (2018, June 21). The deepest reason why modern JavaScript frameworks exist. Medium. https://medium.com/dailyjs/the-deepest-reason-why-modern-javascript-frameworks-exist-933b86ebc445
- Wieruch, R. (2019, March 18). React Function Components. RWieruch. https://www.robinwieruch.de/react-function-component/#react-arrow-function-component
- Incode Group. (2018, May 30). React.js: What’s so good about the front end technology of Facebook? Medium. https://medium.com/@incodegroup/react-js-whats-so-good-about-the-front-end-technology-of-facebook-657f1267af1e#:%7E:text=Thankfully%20Facebook%20released%20React%20as,blended%20in%20the%20application%20code.

