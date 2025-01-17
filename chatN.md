# Async Thunks vs Promises with `resolve` and `reject`

An **async thunk** is a function that returns another function, often used in Redux for handling asynchronous operations. It simplifies the process of dispatching actions based on asynchronous results. Here's how it compares to using a `Promise` with `resolve` and `reject`:

## 1. Promise with `resolve` and `reject`
- You manually create a promise using `new Promise((resolve, reject) => {...})`.
- Inside the promise, you perform asynchronous operations and call `resolve` to fulfill the promise or `reject` to handle errors.

**Example:**
```javascript
const myPromise = new Promise((resolve, reject) => {
  asyncOperation()
    .then(result => resolve(result))
    .catch(error => reject(error));
});

const myAsyncThunk = () => {
  return async (dispatch) => {
    try {
      const result = await asyncOperation();
      dispatch(successAction(result));
    } catch (error) {
      dispatch(failureAction(error));
    }
  };
};


