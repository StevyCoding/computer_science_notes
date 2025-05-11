- middle ware for redux
- allow to write action creator that return function instead of an action
- useful to handle asynchronous operations such as fetchin data from an API
example of Redux Thunk
1. **Middleware in Redux**: Middleware provides a way to interact with actions that have been dispatched to the store before they reach the reducer. Redux Thunk is one of the popular middleware solutions for Redux.
    
2. **Handling Asynchronous Actions**: Redux Thunk enables you to dispatch functions, which can delay the dispatch of an action, or dispatch multiple actions. This is particularly useful for handling asynchronous operations, such as making API requests. Without Redux Thunk, Redux only accepts plain object actions.
    
3. **Thunk Action Creators**: Thunk action creators are functions that return another function. The inner function receives the store's dispatch method, which can then be used to dispatch regular actions, including those that may be created as a result of asynchronous operations.
```js
const fetchData = () => {
  return (dispatch) => {
    dispatch({ type: 'FETCH_DATA_REQUEST' });
    // Perform asynchronous operation, e.g., fetching data from an API
    api.getData().then((data) => {
      dispatch({ type: 'FETCH_DATA_SUCCESS', payload: data });
    }).catch((error) => {
      dispatch({ type: 'FETCH_DATA_FAILURE', payload: error });
    });
  };
};
```
4. **Integration with Redux Store**: You can integrate Redux Thunk with the Redux store by applying it as middleware when creating the store.
```js
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers';

const store = createStore(rootReducer, applyMiddleware(thunk));
```

Redux Thunk simplifies the process of handling asynchronous operations in Redux by providing a way to write action creators that return functions. This makes it easier to manage complex asynchronous logic and handle side effects in your Redux applications.
