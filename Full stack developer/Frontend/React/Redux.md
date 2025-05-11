- State management tool

# State

- stored in a single JavaScript object
- is immutable, meaning whenever a change is  made, a new object is created instead of modifying the old one
- more info in [[State]]

# Actions

-  plain JavaScript objects
- describe change you want to the state
- always have a **type** field
- might have additional data

# Reducers

- pure functions
- describe how the application state should change, in response of an action
- take current state and return new state

## example of state

```js
export const Dishes = (
  state = {
    isLoading: true,
    errMess: null,
    dishes: [],
  },
  action
) => {
  switch (action.type) {
    case ActionTypes.ADD_DISHES:
      return {
        ...state,
        isLoading: false,
        errMess: null,
        dishes: action.payload,
      };

    case ActionTypes.DISHES_LOADING:
      return { ...state, isLoading: true, errMess: null, dishes: [] };
    case ActionTypes.DISHES_FAILED:
      return {
        ...state,
        isLoading: false,
        errMess: action.payload,
        dishes: [],
      };

    default:
      return state;
  }
};
```

# Store

- where the app  state is actually held.
- container for a state
- provide methods  
	- **dispatch** to send actions to the store
	- **getState**  to retrieve current state

![[ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26-1.gif]]