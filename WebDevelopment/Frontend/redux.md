# Redux
- Redux is a specification
- Redux core concepts:
  1. **Store**
  2. **Action**
  3. **Reducer**
```
Analogy with shop example:
1. Store -- shop  (holds the state of application)
2. Action -- intention to buy a cake (describes what happened)
3. Reducer -- shopkeeper (ties the 'store' and 'actions' together.

In short redux has:
1. A **Store** that holds the state of the app.
2. An **Action** that describes the changes in the state of the application.
3. A **Reducer** which actually carries out state transition depending on the action.
```
### Action:
 Actions describes what happened but they donot describe how the application state changes. Reducers take care of state changes
 in according to an action.

### Reducers:
  1. Reducers specify how the application's state changes in response to actions sent to the store.
  2. Reducers in general is a function that accepts state and action as arguments, and returns the next state of the app.
  
     `(previousState, action) => newState`
