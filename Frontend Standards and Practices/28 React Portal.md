# React Portal

Normally, when you return an element from a component’s render method, it’s mounted into the DOM as a child of the nearest parent node:

#### Sample:
in *public/index.html* setup your element id where you want to render your element.
```
<div id="portal"></div>
```

*setup Create Portal*
```
export default function Modal({ open, children, onClose }) {
  if (!open) return null

  return ReactDom.createPortal(
    <>
      <div style={OVERLAY_STYLES} />
      <div style={MODAL_STYLES}>
        <button onClick={onClose}>Close Modal</button>
        {children}
      </div>
    </>,
    document.getElementById('portal')
  )
```

Note: the component will render to `<div id="portal"></div>`
