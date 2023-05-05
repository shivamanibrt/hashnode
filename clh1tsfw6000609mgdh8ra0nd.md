---
title: "React UseEffect and UseState in react."
datePublished: Sat Apr 29 2023 10:14:07 GMT+0000 (Coordinated Universal Time)
cuid: clh1tsfw6000609mgdh8ra0nd
slug: react-useeffect-and-usestate-in-react
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/UYsBCu9RP3Y/upload/dec302518d2b780008d48129576f8516.jpeg

---

React is a way to build cool web pages and apps using a special language called JavaScript. It's like playing with building blocks but on a computer!

One of the important things you can do with React is called "state". State is like a magic box where you can put things that can change over time, like how many points you have in a game, or how many times you've clicked a button.

To help you use state, React has something called "hooks". A hook is like a special tool that makes it easy to put things in the magic box and take them out again when you need them.

One of the hooks you might use is called "useState". It's like a way to make a new magic box and put things inside it. For example, you could use useState to make a magic box for counting how many times you've clicked a button.

Overall, React and its hooks are a really cool way to build things on the computer and make them do fun stuff!

To use useState, you first need to import it from the React library:

```plaintext
import React, { useState } from 'react';
```

Then, you can declare a state variable and initialize it with a default value:

```javascript
const [count, setCount] = useState(0);
```

In this example, the state variable is called `count`, and its initial value is 0. The `useState` hook returns an array with two elements: the current state value (`count`) and a function to update the state (`setCount`).

You can then use `count` and `setCount` in your component to display and update the state value:

```javascript
return (
  <div>
    <p>You clicked {count} times</p>
    <button onClick={() => setCount(count + 1)}>
      Click me
    </button>
  </div>
);
```

In this example, a paragraph displays the current value of `count`, and a button updates the value when clicked by calling the `setCount` function with the new value.

## **Use Effect**

In React, `useEffect` is a built-in hook that allows you to perform side effects in function components. A side effect is any code that affects something outside the scope of the current function, such as manipulating the DOM, making API requests, or setting up event listeners.

The `useEffect` hook accepts two parameters: a function that contains the side-effect code and an optional array of dependencies. Here's an example:

```javascript
javascriptCopy codeimport React, { useState, useEffect } from 'react';

function Fract() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

In this example, the `useEffect` hook is used to update the document title whenever the `count` state variable changes. The function passed to `useEffect` is called an "effect function" and it updates the document title by using the `document.title` property.

The second parameter of `useEffect` is an array of dependencies, which determines when the effect function should be called. If a dependency changes, the effect function will be called again. In this example, the `count` the state variable is the only dependency, so the effect function will be called every time `count` changes.

Overall, `useEffect` is a powerful tool that allows you to perform side effects in function components and manage the lifecycle of your components. It is particularly useful for handling asynchronous operations, such as fetching data from an API or setting up event listeners.