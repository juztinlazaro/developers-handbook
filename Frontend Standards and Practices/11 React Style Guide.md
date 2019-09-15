# React Style Guide

Airbnb has written a really nice style guide for ES6 here. We follow Airbnb's JavaScript style guide, with some special additional conventions for React code in future.

### Importing

#### Alignment of Import Statements

Do not align the from <package> in import statements as they are troublesome to realign when new import statements are added and do not serve much purpose besides aesthetics. Import specific package from specific folder path.

```
// Bad
import _        from 'lodash';
import $        from 'jquery';
import { Button } from 'antd';
import React    from 'react';
import Router   from 'react-router';

// Good
import _map from 'lodash/map';
import $ from 'jquery';
import Button from 'antd/lib/button';
import React from 'react';
import Router from 'react-router';
```

### Classes

#### Component Naming

Component class names should always begin with an upper case character. React expects elements starting with a lower case character to be built-in HTML elements and will throw an error if your component starts with one.

```
// Bad
class myComponent extends React.Component {

// Good
import React, { Component } from 'react'
class MyComponent extends Component {
```

### File Naming

File names for components should be in CamelCase and follows the class name (JS) of the component such as

```
 // Bad
 my-component.jsx.

// Good
MyComponent.jsx
```

### Methods Ordering

#### Methods should generally be ordered by the following:

- constructor
- Lifecycle methods in order of first to last
- Custom methods
- render
- props and context

```
class MyComponent extends React.Component {
  constructor: function () {}
  componentWillMount : function () {}
  componentWillUnmount : function () {}
  handleButtonClick : function () {}
  myCustomMethod: function () {}
  render : function () {}
});


MyComponent.propTypes = {};
MyComponent.defaultProps = {};
MyComponent.contextTypes = {};
```

### Declaring Props

Always define the component's props in a propTypes object. This makes it easy to quickly see all of the props that are used in the component, gives the reader an idea of what the component does, and adds validation to incoming props on a new instance. Comment these props generously and alphabetize them if there are many.

example:

```
import PropTypes from 'prop-types';

class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

Greeting.propTypes = {
  name: PropTypes.string,
};

Greeting.defaultProps = {
  name: '',
};

```

### Method Naming

Event handlers should be named as `handle{EventName}`. Props that pass event handlers should be named as `on{EventName}`.
Note: `dont be generic on naming, please be more descriptive in naming`

```
// good
handleButtonClick = () => { ... }

<Component onButtonClick={this.handleButtonClick.bind(this)} />

// better
handleCompleteBtnClick = () => { ... }

<Component onCompleteBtnClick={this.handleCompleteBtnClick .bind(this)} />
```

### Double Quotes for Attributes

Following the convention of HTML, we use double quotes " for attribute strings in JSX.

```
// Bad
<p className='content'>This is some text.</p>

// Good
<p className="content">This is some text.</p>
```

### camelCase for Props

props can also be seen as attributes, and the convention set by React is to use camelCase for JSX attributes.

```
// Bad
<MyComponent status-text="content"/>

// Good
<MyComponent statusText="content"/>
```

### JSX as a Variable or Return Value

JSX variables should be wrapped in parentheses regardless of number of lines.

```
// Multi-line example
var multilineJsx = (
  <header>
    <Logo />
    <Nav />
  </header>
);

// Single-line example
var singleLineJsx = (
  <h1>Simple JSX</h1>;
);
```

### Formatting Attributes

For elements with attributes that cannot fit into a single line, a cleaner and easier indentation would be to indent each attribute on a separate line as opposed to aligning attributes after the tag, which is still more readable than no indentation, but takes a little more attention than it should.

```
// Bad
<input type="text"
       value={this.state.newDinosaurName}
       onChange={this.inputHandler.bind(this, 'newDinosaurName')} />

// Good
<input
  type="text"
  value={this.state.newDinosaurName}
  onChange={this.inputHandler.bind(this, 'newDinosaurName')}
/>
```

### Avoid using let for data manipulation, always use const for functional programming

### When to use IIFE & Arrow Functions

### When to use state & props

### Avoid data manipulation inside render function

### When to use PureComponent & Component class

### Implement Folder Patterns
