---
title: "How to Quickly Add Toast Notifications to Your React App with React Toastify?"
seoTitle: "Adding Toast Notifications to Your React App: Guide to React Toastify"
seoDescription: "Add customizable toast notifications to your React app with ease using React Toastify. Improve your user experience today"
datePublished: Tue May 02 2023 01:39:39 GMT+0000 (Coordinated Universal Time)
cuid: clh5lqdi7000009mgcukw03q6
slug: how-to-quickly-add-toast-notifications-to-your-react-app-with-react-toastify
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/MIbQuo8EWCo/upload/ad3e3de1915ac08f626e83e0e6c085ef.jpeg
tags: reactjs, react-toast

---

React Toastify is a popular library for displaying toast notifications in a React application. Here's a step-by-step guide on how to connect React Toastify to your React application:

### Install React Toastify using npm or yarn:

```javascript
npm install react-toastify
```

or

```javascript
yarn add react-toastify
```

### Import the necessary components from React Toastify into your React application:

```javascript
import { ToastContainer, toast } from 'react-toastify';
import 'react-toastify/dist/ReactToastify.css';
```

### Render the ToastContainer component in your React application:

```javascript
function App() {
  return (
    <div>
      <ToastContainer />
      ...
    </div>
  );
}
```

### Use the `toast` function to display a notification:

```javascript
function handleClick() {
  toast('Hello World!');
}

function App() {
  return (
    <div>
      <ToastContainer />
      <button onClick={handleClick}>Click Me</button>
    </div>
  );
}
```

### Customize the notification by passing options to the `toast` function:

```javascript
function handleClick() {
  toast.success('Hello World!', {
    position: toast.POSITION.TOP_RIGHT
  });
}

function App() {
  return (
    <div>
      <ToastContainer />
      <button onClick={handleClick}>Click Me</button>
    </div>
  );
}
```

You can find more information about React Toastify, including additional customization options, on the official documentation website: [**https://fkhadra.github.io/react-toastify/**](https://fkhadra.github.io/react-toastify/).