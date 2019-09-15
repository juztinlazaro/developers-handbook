# Components Best Practices

### Ways to create react components

React pure components

### Types of components

| **Container**              | **Presentation**                   |
| -------------------------- | ---------------------------------- |
| Little to no markup        | Nearly all markup                  |
| Pass data and actions down | Receive data and actions via props |
| Know about Redux           | Doesn't know about Redux           |
| Often stateful             | Typically functional components    |

### My presentational components:

1. Are concerned with how things look.
2. May contain both presentational and container components\*\* inside, and usually have some DOM markup and styles of their own.
3. Often allow containment via this.props.children.
4. Have no dependencies on the rest of the app, such as Flux actions or stores.
5. Don’t specify how the data is loaded or mutated.
6. Receive data and callbacks exclusively via props.
7. Rarely have their own state (when they do, it’s UI state rather than data).
8. Are written as functional components unless they need state, lifecycle hooks, or performance optimizations.
   Examples: Page, Sidebar, Story, UserInfo, List.

### My container components:

1. Are concerned with how things work.
2. May contain both presentational and container components\*\* inside but usually don’t have any DOM markup of their own except for some wrapping divs, and never have any styles.
3. Provide the data and behavior to presentational or other container components.
4. Call Flux actions and provide these as callbacks to the presentational components.
5. Are often stateful, as they tend to serve as data sources.
6. Are usually generated using higher order components such as connect() from React Redux, createContainer() from Relay, or Container.create() from Flux Utils, rather than written by hand.
   Examples: UserPage, FollowersSidebar, StoryContainer, FollowedUserList.

Remember, components don’t have to emit DOM. They only need to provide composition boundaries between UI concerns.

### When to Introduce Containers?

When you notice that some components don’t use the props they receive but merely forward them down and you have to rewire all those intermediate components any time the children need more data, it’s a good time to introduce some container components. This way you can get the data and the behavior props to the leaf components without burdening the unrelated components in the middle of the tree.

When we first started writing React, we remember seeing many different approaches to writing components, varying greatly from tutorial to tutorial. Though the framework has matured considerably since then, there doesn’t seem to yet be a firm ‘right’ way of doing things.

#### Before we get started, a couple of notes:

- We use ES6 and ES7 syntax.
- If you’re not sure of the distinction between presentational and container components, we recommend you [[read this first |https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0]].
- Please let us know for any suggestions, questions, or feedback, open an issue [[here | something]]

### Class Based Components

Class based components are stateful and/or contain methods. We try to use them as sparingly as possible, but they have their place.

Let’s incrementally build our component, line by line.

#### Initializing State

```
import React, { Component } from 'react'
import ExpandableForm from './ExpandableForm'

class ProfileContainer extends Component {

  // es7
  state = { expanded: false }

  ......
export default ProfileContainer
```

#### We also make sure to export our class as the default.

### propTypes and defaultProps

```
import React, { Component } from 'react'
import { string, object } from 'prop-types'
import ExpandableForm from './ExpandableForm'


class ProfileContainer extends Component {
  state = { expanded: false }

  static propTypes = {
    model: object.isRequired,
    title: string
  }

  static defaultProps = {
    model: {
      id: 0
    },
    title: 'Your Name'
  }
.....
```

propTypes and defaultProps are static properties, declared as high as possible within the component code. They should be immediately visible to other devs reading the file, since they serve as documentation.

##### Note: All your components should have propTypes.

#### Methods

```
import React, { Component } from 'react'
import { string, object } from 'prop-types'
import ExpandableForm from './ExpandableForm'


class ProfileContainer extends Component {
  state = { expanded: false }

  static propTypes = {
    model: object.isRequired,
    title: string
  }

  static defaultProps = {
    model: {
      id: 0
    },
    title: 'Your Name'
  }
  handleSubmit = (e) => {
    e.preventDefault()
    this.props.model.save()
  }

  handleNameChange = (e) => {
    this.props.model.changeName(e.target.value)
  }

  handleExpand = (e) => {
    e.preventDefault()
    this.setState({ expanded: !this.state.expanded })
  }

```

With class components, when you pass methods to subcomponents, you have to ensure that they have the right this when they’re called. This is usually achieved by passing this.handleSubmit.bind(this) to the subcomponent.

We think this approach is cleaner and easier, maintaining the correct context automatically via the ES6 arrow function.

### Passing setState a Function

In the above example, we do this:

```
this.setState({ expanded: !this.state.expanded })
```

Here’s the dirty secret about setState — it’s actually asynchronous. React batches state changes for performance reasons, so the state may not change immediately after setState is called.

That means you should not rely on the current state when calling setState — since you can’t be sure what that state will be!

Here’s the solution — pass a function to setState, with the previous state as an argument.

```
this.setState(prevState => ({ expanded: !prevState.expanded }))
```

### Destructuring Props

```
import React, { Component } from 'react'
import { string, object } from 'prop-types'
import ExpandableForm from './ExpandableForm'
export default class ProfileContainer extends Component {
  state = { expanded: false }

  static propTypes = {
    model: object.isRequired,
    title: string
  }

  static defaultProps = {
    model: {
      id: 0
    },
    title: 'Your Name'
  }
handleSubmit = (e) => {
    e.preventDefault()
    this.props.model.save()
  }

  handleNameChange = (e) => {
    this.props.model.changeName(e.target.value)
  }

  handleExpand = (e) => {
    e.preventDefault()
    this.setState(prevState => ({ expanded: !prevState.expanded }))
  }

  render() {
    const {
      model,
      title
    } = this.props
    return (
      <ExpandableForm
        onSubmit={this.handleSubmit}
        expanded={this.state.expanded}
        onExpand={this.handleExpand}>
        <div>
          <h1>{title}</h1>
          <input
            type="text"
            value={model.name}
            onChange={this.handleNameChange}
            placeholder="Your Name"/>
        </div>
      </ExpandableForm>
    )
  }
}
```

Components with many props should have each prop on a newline, like above.

### Creating styles or css

- please read [issue](https://github.com/juztinlazaro/developers-paperback/issues/new)

```
import React, { Component } from 'react'
import { string, object } from 'prop-types'
import ExpandableForm from './ExpandableForm'
export default class ProfileContainer extends Component {
 ....
 ......
 .......

 render() {
    const {
      model,
      title
    } = this.props
    return (
      <section className="Parent-section">
       <ExpandableForm
        onSubmit={this.handleSubmit}
        expanded={this.state.expanded}
        onExpand={this.handleExpand}>
        <div className="input-container">
          <h1 className="title -text-pumpkin">{title}</h1>
          <input
            className="input-name"
            type="text"
            value={model.name}
            onChange={this.handleNameChange}
            placeholder="Your Name"/>
        </div>
       </ExpandableForm>
      </section>
    )
  }
}

```

### Closures

Avoid passing new closures to subcomponents, like so:

```
          <input
            type="text"
            value={model.name}
            // onChange={(e) => { model.name = e.target.value }}
            // ^ Not this. Use the below:
            onChange={this.handleChange}
            placeholder="Your Name"/>
```

Here’s why: every time the parent component renders, a new function is created and passed to the input.

Reconciliation is the most expensive part of React. Don’t make it harder than it needs to be! Plus, passing a class method is easier to read, debug, and change.

_Here’s our full component:_

```
import React, { Component } from 'react'
import { string, object } from 'prop-types'
// Separate local imports from dependencies
import ExpandableForm from './ExpandableForm'
import './styles/ProfileContainer.css'

// Use decorators if needed
@observer
export default class ProfileContainer extends Component {
  state = { expanded: false }
  // Initialize state here (ES7) or in a constructor method (ES6)

  // Declare propTypes as static properties as early as possible
  static propTypes = {
    model: object.isRequired,
    title: string
  }

  // Default props below propTypes
  static defaultProps = {
    model: {
      id: 0
    },
    title: 'Your Name'
  }

  // Use fat arrow functions for methods to preserve context (this will thus be the component instance)
  handleSubmit = (e) => {
    e.preventDefault()
    this.props.model.save()
  }

  handleNameChange = (e) => {
    this.props.model.name = e.target.value
  }

  handleExpand = (e) => {
    e.preventDefault()
    this.setState(prevState => ({ expanded: !prevState.expanded }))
  }

  render() {
    // Destructure props for readability
    const {
      model,
      title
    } = this.props
    return (
      <ExpandableForm
        onSubmit={this.handleSubmit}
        expanded={this.state.expanded}
        onExpand={this.handleExpand}>
        // Newline props if there are more than two
        <div>
          <h1>{title}</h1>
          <input
            type="text"
            value={model.name}
            // onChange={(e) => { model.name = e.target.value }}
            // Avoid creating new closures in the render method- use methods like below
            onChange={this.handleNameChange}
            placeholder="Your Name"/>
        </div>
      </ExpandableForm>
    )
  }
}
```

### Also, when you only want to render an element on one condition, instead of doing this…

```
{
  isTrue
   ? <p>True!</p>
   : <none/>
}
```

… use short-circuit evaluation:

```
{
  isTrue &&
    <p>True!</p>
}
```

For more info.. [[here | https://engineering.musefind.com/our-best-practices-for-writing-react-components-dec3eb5c3fc8]]
