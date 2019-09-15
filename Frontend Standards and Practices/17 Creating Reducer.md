# Creating Reducer

- Use handleActions in `redux-actions`
- create model(initial state)
- file name with name space of reducer
- importing actions, we use webpack alias for action,

```
 instead of

 import * as ACTIONS from '../../../actions/todo/todo.action'';

 use

 import * as ACTION from 'Actions/todo/todo.action';
```

Model.js

```
export default {
  todos: [],
  error: [],
  loading: false,
};
```

todo.reducer.js

```
import { handleActions } from 'redux-actions'
import * as ACTION from 'Actions/todo/todo.action';
import Model from './model';

export default handleActions({
  [ACTION.getTodoSuccess]: (state, action) => ({
    ...state,
    todos: action.payload,
    loading: false,
  }),
  [ACTION.getTodoLoading]: (state, action) =>({
    ...state,
    loading: true,
  }),
  [ACTION.getTodoError]: (state, action) => ({
    ...state,
    error: action.payload,
    loading: false,
  })[ACTION.getTodoCancel]: (state, action) => ({
    ...state,
    loading: false,
  }),}, Model);
```

### Reducers

Forbidden in Reducers

1. Mutate arguments
2. Perform side effects
3. Call non-pure functions

Write independent small reducer functions that are each responsible for updates to a specific slice of state. We call this pattern "reducer composition". A given action could be handled by all, some, or none of them. -REDUX FAQ
