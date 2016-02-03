---
layout: page
title: React
permalink: /react/
---

## React on ES6+

- [class definition syntax](https://babeljs.io/docs/learn-es2015/#classes)
- Class methods are declared without a colon, `function` keyword, and comma
- All of the lifecycle methods but one can be defined as you would expect when using the new `class` syntax. The `constructor` method now assumes role of `componentWillMount`

```js
class Photo extends React.Component {
  render() {
    return <img alt={this.props.caption} src={this.props.src} />;
  }
}
```

```js
// The ES5 way
var Photo = React.createClass({
  handleDoubleTap: function(e) { … },
  render: function() { … },
});

// ES6 way
class Photo extends React.Component {
  handleDoubleTap(e) { … }
  render() { … }
}

```

## Lifecycle Methods

- Children get their `props` from their parent, but manage their own state.
- Loose analogy: `props` are public properties; `state` are private properties.
- Lifecycle methods fire top down before render, bottom up after render. For example, `componentWillMmount` will fire in a parent component before it fires in a child component. Once rendered, `componentDidMount` is fired on the lowest child component, and then up the chain.

Various methods are executed at specific points in a component's lifecycle:

1. `componentWillMount` (in ES6+, this is now replaced by `constructor` method)

2. `componentDidMount`
  - Invoked once, only on the client (not on the server), immediately after the initial rendering occurs.
  - At this point in the lifecycle, you can access any refs to your children (e.g., to access the underlying DOM representation).
  - The `componentDidMount()` method of child components is invoked before that of parent components.
  - f you want to integrate with other JavaScript frameworks, set timers using setTimeout or setInterval, or send AJAX requests, perform those operations in this method

3. `componentWillReceiveProps`
  - Invoked when a component is receiving new props. This method is not called for the initial render.
  - Use this as an opportunity to react to a prop transition before `render()` is called by updating the state using `this.setState()`.
  - The old props can be accessed via this.props. Calling `this.setState()`within this function will not trigger an additional render.

4. `shouldComponentUpdate`
  - Invoked before rendering when new props or state are being received
  - This method is not called for the initial render or when `forceUpdate` is used.
  - Use this as an opportunity to return `false` when you're certain that the transition to the new props and state will not require a component update.
  - By default, `shouldComponentUpdate` always returns true to prevent subtle bugs when state is mutated in place, but if you are careful to always treat state as immutable and to read only from `props` and `state` in `render()` then you can override `shouldComponentUpdate` with an implementation that compares the old props and state to their replacements.
  - If performance is a bottleneck, especially with dozens or hundreds of components, use `shouldComponentUpdate` to speed up your app.

5. `componentWillUpdate`
  - Invoked immediately before rendering when new props or state are being received. This method is not called for the initial render.
  - Use this as an opportunity to perform preparation before an update occurs.

6. `componentDidUpdate`
  - Invoked immediately after the component's updates are flushed to the DOM. This method is not called for the initial render.
  - Use this as an opportunity to operate on the DOM when the component has been updated.

7. `componentWillUnmount`
  - Invoked immediately before a component is unmounted from the DOM.
  - Perform any necessary cleanup in this method, such as invalidating timers or cleaning up any DOM elements that were created in `componentDidMount`.

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

## Reference

- [React Component Specs and Lifecycle](https://facebook.github.io/react/docs/component-specs.html)
