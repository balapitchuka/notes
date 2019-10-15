# Redux

### Action:
 Actions describes what happened but they donot describe how the application state changes. Reducers take care of state changes
 in according to an action.

### Reducers:
  1. Reducers specify how the application's state changes in response to actions sent to the store.
  2. Reducers in general is a function that accepts state and action as arguments, and returns the next state of the app.
  
     `(previousState, action) => newState`
