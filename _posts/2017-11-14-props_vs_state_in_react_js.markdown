---
layout: post
title:      "Props vs. State in React JS"
date:       2017-11-14 23:54:01 +0000
permalink:  props_vs_state_in_react_js
---


This blog post seeks an answer to a pretty basic question “What is the difference between state and props in React?” that for some reason left me puzzled when I had faced it.

**Props**

Let’s start by defining Component’s props (obviously short for properties) in React. Props are used to customize Component when it’s being created and give it different parameters.

```
import React, {Component} from 'react'
class Topic extends Component {
   render{
     return(
      <div>
        {this.props.name}
      </div>
    )
   }
}
```

One of the most important features of props is that they can be passed by a parent component to its child components. This allows us to create a component that can be customised with a new set of props every time we use it.

```
import React, {Component} from 'react'
class Welcome extends Component {
   render{
     return(
      <div>
        <p> Welcome to React, today you will learn: </p>
        <Topic name="Props"/>
        <Topic name="State"/>
      </div>
    )
   }
}
```

Props are passed to the component and are fixed throughout its lifecycle. But there are cases when we want to use data that we know is going to change overtime. In this case we use something called state.

**State**

Unlike props, state is a private feature and it strictly belongs to a single Component. State allows React components to dynamically change output over time in response to certain events.

Component’s state is initialized inside a constructor:

```
class Counter extends Component{
  
  constructor(props){
    super(props);
    this.state = {counter: 0}
  }
  render(){
    return(
      <p>{this.state.counter}</p>
  )
}
```

And can be changed later using inbuilt setState() function.

```
class Counter extends Component{
  
  constructor(props){
    super(props);
    this.state = {counter: 0}
    this.increment = this.increment.bind(this);
  }
  increment(){
    this.setState({counter: this.state.counter + 1})
  }
render(){
    return(
      <button onClick={this.increment}>Like</button>
      <p>{this.state.counter}</p>
  )
}
```

**Conclusion**

From the examples above we can see that state looks and works a lot like props, but it is contained within a single component and can be changed as we please, while props are read-only for their owning Component.

An important thing to mention, however, is that when it comes to implementing Redux in your app, the state is created once for the root component and then accessed in a read-only format by other components using mapStateToProps.

***

Sources:
[https://reactjs.org/docs/components-and-props.html](http://)
[http://www.hackingwithreact.com/read/1/10/state-vs-props-in-react](http://)

