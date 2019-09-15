# CSS Style Guide

## Styling CSS without losing your sanity

We follow Reasonable System for CSS Stylesheet Structure [rscss](http://rscss.io/).

## Rules

### Be semantic

`MaintainableCSS` is an approach to writing modular, scalable and maintainable CSS. Not only does this guide explain how to do this, but more importantly it explains why.

This is not a library or framework. It’s a set of principles, guides and conventions to help you write CSS for small or large-scale websites.

##### What does maintainable mean?

Maintainable CSS can be defined as being able to make styling changes, without worrying about accidentally causing problems elsewhere.

##### What does scalable mean?

Scalable CSS means that as CSS increases in size, it’s still easy to maintain. If you’ve ever inherited a large CSS codebase, and been afraid to make changes, you’ll sympathise with this.

##### What does modular mean?

A module is a distinct, independent unit that can be combined with other modules to form a more complex structure. In a living room, we can consider the TV, the sofa and the wall art to be modules, all coming together to create a room.

If we take one of the units away, the others still work. We don’t need the TV to be able to sit on the sofa etc. In a website the header, registration form, shopping basket, article, product list, navigation and homepage promo can all be considered to be modules.

Please check the [Documentation](https://maintainablecss.com/chapters/) here.

### 3 level nesting

- first level Parent element
- second level Child element
- Pseudo-classes

```
 // Good
 .Parent-Component-section { // first level parent section
   .....

   .child-component { // second level child section
     ....
     &:hover { // third level Pseudo-classes
       ....
     }

     &:focus { // third level Pseudo-classes
       ....
     }
   }
 }



 .Parent-component-section {
    ....
    .child-component {
     ...
    }

    .child-component > .button-element {
      ....
    }

    .child-component > .button-element {
      ....
    }

    .child-component > .button-element > .something-class {
      ....
    }

    .todo .list .item {
      ...
    }

    .todo .list .item .ui-button {
      ...

      &:hover {
        ...
      }
    }
 }
```

#### Avoid multi-level nesting

```
  // bad
  .Parent-Component-section {
     ...
     .child-component {
        ...
        .button-element {
          ....

          &:hover {
           ....
          }

          .something-class {
            ....
          }

          .todo-list {
            ...

             .todo-item {
                ...
             }
          }
        }
     }
  }

```

# [Semantic](https://maintainablecss.com/chapters/semantics/)

### Here’s the same thing using semantic classes:

```
<div class="hero">
  <h1 class="hero-title">Heading</h1>
  <p class="hero-tagline">Tagline</p>
</div>
```

#### Notes:

- These classes are easy to read. No mental mapping is required.
- The content is no longer obfuscated.
- We know where the module begins and ends.
- The HTML is half the size.
- It’s easy to read the CSS (in the inspector or in the file) because it has dedicated language constructs that exist for this purpose.

### Because it’s easier to build responsive sites

```
<div class="grid clearfix">
  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
</div>
```

#### Notes:

- There are 7 classes, some of which override each other.
- To make the columns actually responsive we would need a fs3large class etc. This means using a naming convention that recreates language constructs found in CSS.
- At certain break points, the classes are misleading and redundant. For example .clearfix doesn’t clear on small screens.

#### Because styling state is easier

Consider the following HTML:

```
<a class="padding-left-20 red" href="#"></a>
```

### Conventions

```
.<module>[-<component>][-<state>] {}
```

Square brackets are optional depending on the module in question. Here are some examples:

```
/* Module container */
.searchResults {}

/* Component */
.searchResults-heading {}

/* State */
.searchResults-isLoading {}
```

Notes:

- component and state are both delimited by a dash
- names are written with lowerCamelCase
- selectors are prefixed with the module name

### Why must I prefix the module name?

Good question. Here’s some HTML without a prefix:

```
<div class="basket">
  <div class="heading">
```

And the CSS:

```
/* module */
.basket {}

/* heading component of basket module */
.basket .heading {}
```

There are two problems:

1. when viewing HTML, it’s hard to differentiate between a module and a component; and

2. the .basket .heading component will inherit styles from the .heading module which has unintended side effects.

# Classnames

A simple JavaScript utility for conditionally joining classNames together.

```
npm install classnames --save
```

## Usage

One of its primary use cases is to make dynamic and conditional className props simpler to work with (especially more so than conditional string manipulation).

### Example:

```
<div
  className={classnames('details-wrapper', {
    'has-error': validateRequiredRole || validateRequiredRoleZero,
  })}
>
```

### [Read and Know more about Classnames](https://www.npmjs.com/package/classnames)
