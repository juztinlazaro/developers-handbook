# useCallback

Pass an inline *callback and an array of dependencies*. *useCallback* will return a *memoized version of the callback that only changes if one of the dependencies has changed*. This is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders *(e.g. shouldComponentUpdate)*.

```
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```

# useMemo
```
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

Pass a “create” function and an array of dependencies. *useMemo will only recompute the memoized value when one of the dependencies has changed*. This optimization helps to avoid expensive calculations on every render.

Remember that the function passed to useMemo runs during rendering. Don’t do anything there that you wouldn’t normally do while rendering. For example, side effects belong in useEffect, not useMemo.

*If no array is provided, a new value will be computed on every render.*

**You may rely on useMemo as a performance optimization, not as a semantic guarantee.** In the future, React may choose to “forget” some previously memoized values and recalculate them on next render, e.g. to free memory for offscreen components. Write your code so that it still works without useMemo — and then add it to optimize performance.

# useRef
```
const refContainer = useRef(initialValue);
```
useRef returns a mutable ref object whose .current property is initialized to the passed argument (initialValue). The returned object will persist for the full lifetime of the component.

```
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

Note:
Keep in mind that useRef doesn’t notify you when its content changes. Mutating the .current property doesn’t cause a re-render. If you want to run some code when React attaches or detaches a ref to a DOM node, you may want to use a callback ref instead.

