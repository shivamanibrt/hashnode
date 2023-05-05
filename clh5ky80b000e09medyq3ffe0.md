---
title: "How do I Connect my redux store to react?"
seoTitle: "Connecting Redux Store to React: Simple Guide"
seoDescription: "Learn how to connect a Redux store to your React application and manage your state more efficiently with this simple guide."
datePublished: Tue May 02 2023 01:17:45 GMT+0000 (Coordinated Universal Time)
cuid: clh5ky80b000e09medyq3ffe0
slug: how-do-i-connect-my-redux-store-to-react
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/gy08FXeM2L4/upload/ebd023755830f393a4d2bc5aa0f1a706.jpeg
tags: reactjs, redux, redux-toolkit

---

Connecting a Redux store to a React application is a common task for developers using these technologies together. Here's a step-by-step guide on how to connect a Redux store to a React app:

1. Install dependencies: First, you need to install the required dependencies. You will need to install react-redux, which provides the `Provider` component to pass the store down to the component hierarchy, and `redux`, which provides the store itself. You can install both of these with the following command:
    

```javascript
npm install react-redux redux
```

1. Create a Redux store: Next, you need to create a Redux store. You can do this by creating a file called `store.js` and importing `createStore` from the `redux` library. Here's an example of how to create a simple store with a single reducer:
    

```javascript
import { createStore } from 'redux';

const initialState = {
  count: 0
};

function reducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

const store = createStore(reducer);

export default store;
```

1. Provide the store to the app: Now that you have a store, you need to provide it to your React app. To do this, you can use the `Provider` component from `react-redux`. Wrap your entire app in the `Provider` component and pass the store as a prop. Here's an example:
    

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

1. Connect components to the store: Finally, you need to connect your React components to the store. To do this, you can use the `connect` function from `react-redux`. This function takes two arguments: a `mapStateToProps` function and a `mapDispatchToProps` function. The `mapStateToProps` function maps state from the store to props for your component, and the `mapDispatchToProps` function maps actions to props for your component. Here's an example:
    

```javascript
import React from 'react';
import { connect } from 'react-redux';

function Counter(props) {
  return (
    <div>
      <h1>{props.count}</h1>
      <button onClick={props.increment}>+</button>
      <button onClick={props.decrement}>-</button>
    </div>
  );
}

function mapStateToProps(state) {
  return {
    count: state.count
  };
}

function mapDispatchToProps(dispatch) {
  return {
    increment: () => dispatch({ type: 'INCREMENT' }),
    decrement: () => dispatch({ type: 'DECREMENT' })
  };
}

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(Counter);
```

In this example, the `Counter` the component is connected to the store using `connect`. The `mapStateToProps` function maps the `count` property from the store's state to the `count` prop for the component, and the `mapDispatchToProps` function maps the `increment` and `decrement` actions to the `onClick` handlers for the buttons.

To sum up, connecting a Redux store to a React app is a crucial step in building a scalable and maintainable application. It involves installing dependencies, creating a Redux store, providing the store to the app using the `Provider` component, and connecting React components to the store using the `connect` function. This process provides a centralized location for storing and updating the application state, making it easier to manage and scale the app. By implementing these steps, you can take full advantage of the benefits that Redux and React offer, ultimately resulting in a more efficient and maintainable application.