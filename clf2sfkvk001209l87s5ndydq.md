---
title: "Types of the Input field in forms in React"
datePublished: Fri Mar 10 2023 17:04:29 GMT+0000 (Coordinated Universal Time)
cuid: clf2sfkvk001209l87s5ndydq
slug: types-of-the-input-field-in-forms-in-react
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Nl79ckrM_1Q/upload/3a46df4607b39fa345ca063a6dfefd63.jpeg
tags: reactjs, react-form

---

In React, there are two main types of input fields based on control - controlled input fields and uncontrolled input fields.

1\. **Controlled input fields:** A controlled input field is one where the value entered by the user is managed and updated by the application or website itself. For example, if you're filling out a form and you enter your name in a controlled input field, the website might automatically format your name so that the first letter of each word is capitalized. This helps ensure consistency and accuracy of the data entered by the user.

2\. **Uncontrolled Input field:** An uncontrolled input field is one where the value entered by the user is not managed by the application or website. For example, if you're filling out a form and you enter your name in an uncontrolled input field, the website might not do anything to the formatting of your name, which could result in inconsistent data entry.

## How to get data from each of them?

### let's go with the Controlled Input field in forms

use a "state" variable and an "onChange" event handler to get the value from a controlled input field.

So here

\- we use the **OnChange** event handler

\- where the value is stored in a variable function named **handelonChange**

\- which targets the value using event.target.value and stores that value in data

\- and stores the updated value at inputValue updating from setInputValue function.

```javascript
import React, { useState } from 'react';

export const SearchForm = () => {
  const [inputValue, setInputValue] = useState('');

  function handleChange(e) {
    const data =  e.target.value; 
    setInputValue({inputValue,data});
  }

  return (
    <form>
      <label>
        Name:
        <input type="text" value={inputValue} onChange={handleChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}
```

### What about the Uncontrolled input field in forms?

we use 'ref' which is a special attribute in React that allows us to get a reference to a DOM element.

Create a variable named strRef and use hook useRef with an empty variable. Now simply bind strRef with ref in Javascript inside the function field from where the data will pass to the useRef and take the data creating handelOnSubmit function once the submit happens. Now store the value in the variable of your name choice eg: str and assign strRef.current.value which is also similar to the event.target.

Remember strRef is just a variable name that can be anything

```javascript
import { useRef } from 'react';

export const SearchForm = () => {

    const strRef = useRef('');

    const handelOnSubmit = e => {
        e.preventDefault()
        //this gets the actual value
        const str = strRef.current.value;
    }

    return (

        <Form onSubmit={handelOnSubmit} >
           <Form.Control ref={strRef} placeholder='Search by title'/>
            <Button type='submit'>Search Movie </Button>
        </Form>

    );
}
```