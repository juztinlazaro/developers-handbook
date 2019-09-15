# Creating Actions

In creating action we use redux-actions, for more info here:

https://github.com/reduxactions/redux-actions

#### Rules:

- camelcase
- if the action is request, create an action of Epic, Success, Error, Loading, and Cancel for managing the redux state.
- aliasing the types must be Uppercase
- We separate GET, POST, DELETE, PATCH, PUT AND DELETE request by command and queries folder.
  ```
   // Folder Structure
    Actions
      - queries -> all get request actions
      - command -> all post, delete, patch, put actions
  ```

```
/// bad

import { createActions } from 'redux-actions'
import * as types from './types';

export const getTodoList = createAction(Types.GET_TODO_LIST_EPIC)
```

```
// good

import { createActions } from 'redux-actions'
import * as TYPES from './types';

export const getTodoListEpic = createAction(TYPES.GET_TODO_LIST_EPIC)
export const getTodoListSuccess = createAction(TYPES.GET_TODO_LIST_SUCCESS)
export const getTodoListError = createAction(TYPES.GET_TODO_LIST_ERROR)
export const getTodoListLoading = createAction(TYPES.GET_TODO_LIST_LOADING)
export const getTodoListCancel = createAction(TYPES.GET_TODO_LIST_CANCEL)
```

#### example epic action

```
export const getTodoEpic = action$ =>
  action$.ofType(TYPES.GET_TODO_EPIC)
   .switchMap(() => {
      const loading = Observable.of(ACTION.getTodoLoading());

     const request = Observable.ajax(getBlogUrl, headers).delay(5000)
        .takeUntil(action$.ofType(TYPES.GET_TODO_CANCEL))
        .map(result => {
          return ACTION.getTodoSuccess(result.response)
        })
        .catch(error => {
          return Observable.of(ACTION.getTodoError(error))
        })
      ;

      return Observable.concat(
        loading,
        request,
      )
   })

```

### always use action cancel in componentWillUnmount

- canceling unintended request.
- saving unnecessary request.

```
componentWillUnmount() {
    this.props.getPostCancel();
  }

```
