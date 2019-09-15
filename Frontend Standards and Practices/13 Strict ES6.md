# Strictly Use of ES6

## Please Use ES6 If You Can

Visit and read the links below for further understanding of the importance of ES6.

### Know everything about ES6 or ECMAScript 6

#### https://github.com/lukehoban/es6features

### List of ES6 Methodologies

#### http://es6katas.org/

### Immutable Update Patterns

#### https://redux.js.org/docs/recipes/reducers/ImmutableUpdatePatterns.html

Example 1:

```
// good
return {
  ...state,
  TodoList: TodoList.concat(todo),
  TodoNames: TodoNames.concat(name)
}

// better
return {
  ...state,
  TodoList: [...TodoList, todo],
  TodoNames: {
     ...todoNames,
     names,
  }
}
```

Example 2:

```
 // good
function todo(tile) {
  return title
}

// better
const todo = title => title
```
