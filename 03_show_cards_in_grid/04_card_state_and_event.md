### Trello

Now that we created our cards all facing up, when the card is clicked nothing happens...

The next feature we want to work on is 'As a player I can click a card to flip it over'.

Move the card from the `Backlog` list to the `Doing` list

---

Nothing is happening because because we are not **listening** for or **handling** the click event on the card.

We will have to use two new features of react - _events_ and _state_.

### What is an event ?

To have an interactive website we need to have events such as clicking, double clicking, hovering, etc. To handle those events we need event handlers, which are functions that run when a certain event occurs.

The following `button` has an `onClick` event handler that logs "you clicked me" to the console every time the button is clicked:

```jsx
<button onClick={() => console.log("you clicked me")}>CLICK ME</button>
```

---

### What is a state?

One of the super powers of React is updating elements on the screen without refreshing the page! In React, we can build a whole app in one page without refreshing it, how amazing is that?!

To do that we will be using a _hook_ called `useState`. The `useState` hook is a function imported from React that give us a _state variable_ and an _update function_ to change that variable. Every time the update function is called, the component will be re-rendered to show the change.

The following component has a `counter` state, initially set to 0. It also has a button that updates the `counter` state, using `setCounter` every time it is clicked. When the `counter` is updated, the component will be re-rendered to show the new `counter` value.

```jsx
import React, { useState } from "react";

const Counter = () => {
  const [counter, setCounter] = useState(0);

  return (
    <div>
      <h1>You clicked the button {counter} times</h1>
      <button onClick={() => setCounter(counter + 1)}>CLICK ME</button>
    </div>
  );
};
```

---

Let's modify our `Card` component to have a `flipped` state.

We'll update this state every time the card is clicked.

Then we'll use this state to "flip" the card by changing the image that's being displayed.

Let's modify the `Card` component as follows:

```jsx
import React, { useState } from "react"; /* 1 */

import cardBack from "../images/CardBack.jpg"; /* 3 */

const Card = ({ card, checkFlipped }) => {
  const [flipped, changeFlip] = useState(false); /* 1 */

  return (
    <div className="col-3 my-1">
        <img
          className="mx-auto"
          src={flipped ? card.front : cardBack} {/* 3 */}
          height="100%"
          width="100%"
          key="back"
          onClick={() => changeFlip(!flipped)} {/* 2 */}
        />
    </div>
  );
};

export default Card;
```

1. We import `useState` and use it to create a `flipped` state with a default value of `false`
2. Whenever the `<img>` element is clicked it calls the `changeFlip` function and passes it the opposite of the current `flipped` state
3. We import the `CardBack.jpg` image and we use the `flipped` state in the `src` to decide whether we're showing the front or the back of the card. This will "flip" the card back and forth every time it's clicked.

---

### Demo

You should now have a grid of cards that are initally all face-up. Clicking on a card "flips" it.

**KHALID ADD A GIF FOR THIS**

---

### Git

```shell
$ git add .
$ git commit -m "Cards can flip"
$ git push
```
