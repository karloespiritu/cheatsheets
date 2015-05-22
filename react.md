---
layout: page
title: React
permalink: /react/
---

## Basic Class

```html
var Hello = React.createClass({
  render: function() {
    return (
      <div className="class">Hello World</div>
    );
  }
});

React.render(<Hello />, document.getElementById('app'));
```
## Initial States

```html
var GreetUser = React.createClass({

  getInitialState: function(){
    return {
      username: '@karloespiritu'
    }
  },

  render: function() {
    return (
      <div>
        Hello {this.state.username}
      </div>
    );
  }
});
```

## Component Lifecycle

Use this built-in functions inside a component class

```html
//triggered once before first render
componentWillMount: function(){
    // Calling setState here does not cause a re-render
    console.log('This will mount in this component');
},

// Triggered once after the first render
componentDidMount: function(){
    // You have now access to this.getDOMNode()
    alert('In Component Did Mount');
},

// Invoked whenever there is a prop change
// Called before render
componentWillReceiveProps: function(nextProps){
    // Not called for the initial render
    // Previous props can be accessed by this.props
    // Calling setState here does not trigger an additional re-render
    alert('In Component Will Receive Props');
},

// Called IMMEDIATELY before a component is unmounted
componentWillUnmount: function(){

render: function(){
  return (
    <div>
      Hello, {this.state.name}
    </div>
  )
}
```

## Lists

```html
var MyList = React.createClass({
  render: function() {
    var item = function(listItem) {
      return <li>{listItem}</li>;
    };
    return <ul>{this.props.items.map(item)}</ul>;
  }
});
```

