# Create constant name for condition state.
 - for readability purposes and clean code its nice to create a constant name for condition state.
 - describe what condition is.
 - describe the purpose of condition.
 - easy to read what the condition is.

#### example
 ```
  if (response.password === db.password) { // good
    ....
  }
  
  const isIncorrectEmail = response.password === db.password; // better
  if (isIncorrectEmail) {
    ....
  }
 ```