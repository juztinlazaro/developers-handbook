# React hooks

### useState
```
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

### useEffect
Cheat sheet for react life cycle -> useEffect

***componentDidMount***, it will only update once it render;
```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, []);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

***componentDidUpdate***, it will only update every changes.
```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

***componentDidUpdate***, it will only update every changes of array params.
```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);
  const [status, setStatus] = useState(false));

  useEffect(() => {
    document.title = `You clicked ${count} times`;
    console.log('count, count);
  }, [count]);

  useEffect(() => {
    console.log('status, status);
  }, [status]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

***componentWillUnmount***, it will trigger when a component is being removed from the dom.
note: There is no special code for handling updates because useEffect handles them by default. It cleans up the previous effects before applying the next effects.
```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);
  const [status, setStatus] = useState(false));

  useEffect(() => {
    document.title = `You clicked ${count} times`;
    console.log('count, count);
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
    ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
     console.log('run something');
    }
  }, []);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

Note:
Note

If you use this optimization, make sure the array includes all values from the component scope (such as props and state) that change over time and that are used by the effect. Otherwise, your code will reference stale values from previous renders. Learn more about how to deal with functions and what to do when the array changes too often.

If you want to run an effect and clean it up only once (on mount and unmount), you can pass an empty array ([]) as a second argument. This tells React that your effect doesn’t depend on any values from props or state, so it never needs to re-run. This isn’t handled as a special case — it follows directly from how the dependencies array always works.

If you pass an empty array ([]), the props and state inside the effect will always have their initial values. While passing [] as the second argument is closer to the familiar componentDidMount and componentWillUnmount mental model, there are usually better solutions to avoid re-running effects too often. Also, don’t forget that React defers running useEffect until after the browser has painted, so doing extra work is less of a problem.

We recommend using the exhaustive-deps rule as part of our eslint-plugin-react-hooks package. It warns when dependencies are specified incorrectly and suggests a fix.