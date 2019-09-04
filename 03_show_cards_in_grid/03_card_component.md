### Creating a Card and Grid Component

`App.js` is getting messy so to clean our code we are going to refactor the `JSX` for an individual card into a separate _component_.

---

### What is a component?

Components are independent segments of code that split the user interface to manageable, cleaner, reusable pieces. You can think of them as customizable HTML elements.

In other words components let your code look cleaner, more understandable and helps you debug and trace your code easily incase of any errors.

A component is defined as a function that returns `JSX`:

```jsx
const Component = () => {
  return (
    <div>
      <h1>I'M A COMPONENT</h1>
    <div>
  )
}
```

---

### What are props?

Props are information that is passed to a component to customize it (what is looks like, how it behaves, etc):

```jsx
const Person = ({name}) => {
  return (
    <div>
      <h1>HELLO I'M {name}</h1>
    <div>
  )
}
```

Props can be values, data or functions.

---

To make our `Card` component, first create a folder in your project and name it `Components`.

In your `Components` folder create a file named `Card.js` which will include your Card component's code.

We will remove some code from the `App.js` and add it to the `Card.js` component to look like the following:

`Cards.js`:

```jsx
import React from "react";

/* 1 */
const Card = ({ card }) => {
  return (
    <div className="col-3 my-1">
      {/* 2 */}
      <img
        className="mx-auto"
        src={card.image}
        height="100%"
        width="100%"
        key="front"
      />
    </div>
  );
};

export default Card; /* 3 */
```

1. We define a `Card` function that recieve a `card` prop. We assume his will be a single card object from our `cards` array.
2. We render the `JSX` for our card (taken from `App.js`). Note that the `src` for `img` on the card comes from the `card.image`. This means every card that we render will show the image for that card.

---

Now that we have a `Card` component, we can rewrite `App.js` to use it instead of hard-coding the `JSX`:

```jsx
import React from "react";
import "./App.css";

//Data
import cards from "./data";

// Card Back Image
import cardBack from "./images/CardBack.jpg";

//Components
import Card from "./Components/Card"; /* 1 */

function App() {
  let cardsGrid = cards.map(card => (
    <Card key={card.id} card={card} />
  )); /* 2, 3 */

  return (
    <div className="App border my-5">
      <div className="container">
        <div className="row">{cardsGrid}</div>
      </div>
    </div>
  );
}

export default App;
```

1. We import the `Card` component
2. Instead of hard-coded `JSX`, we use the `Card` component in our `.map`. Notice how we're passing the `card` we're iterating over into the component as a prop called `card`. This will make `cardsGrid` an array of **unique** `Card` components, each representing a different card form the `cards` array.
3. Notice how we're also passing a `key` prop. This won't affect the way the card looks - it's there to help React manage the rendering of the `Card` components. It's important to add `key`s every time we interate to create a list of components.

---

### Demo

You should still have a grid of cards but each one will now have a unique image

**KHALID ADD AN IMAGE FOR THIS**

---

###Git

```shell
$ git add .
$ git commit -m "Cards component refactor"
$ git push
```
