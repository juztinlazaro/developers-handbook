# Javascript Coding Standard

Hoping as arrived here, you have walked through the section about [Strictly Use of ES6](https://github.com/juztinlazaro/developers-paperback/blob/master/Frontend%20Standards%20and%20Practices/13%20Strict%20ES6.md). Elsewhere, take time and visit the section and it contents.

## Currying

A process to reduce functions of more than one argument to functions of one argument with the help of lambda calculus.

#### Bad Practice:

```
<Button
  title="Edit"
  onClick={() => {this.handlerShowViewEditModal(record)}}
>
```

#### Good Practice:

```
render() {
  createShowViewEditHandler = record => () => {
    return this.handlerShowViewEditModal(record);
  }

  return (
    <Button
      title="Edit"
      onClick={this.createShowViewEditHandler(record)}
    >
  )
}
```

## Destructuring Assignment

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

### Destructuring props Example

Before:

```
init = () => {
 this.services.getProfileSummaryEpic(CLIENTID);
 };
```

After:

```
init = () => {
   const { services } = this.props;
   services.getProfileSummaryEpic(CLIENTID);
 };
```

### Destucturing state Example

Before:

```
handleFieldsValue = () => {
   this.props.form.setFieldsValue({
     email: currentUser.email || '',
     firstName: this.state.currentUser.first_name || '',
     lastName: this.state.currentUserlast_name || '',
   });
 };
```

After:

```
handleFieldsValue = () => {
   const { form } = this.props;
   const { setFieldsValue } = form;
   const { currentUser } = this.state;
   setFieldsValue({
     email: currentUser.email || '',
     firstName: currentUser.first_name || '',
     lastName: currentUserlast_name || '',
   });
 };
```
