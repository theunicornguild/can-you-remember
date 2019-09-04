Obviously, our game won't consist of one card. We want multiple cards.

We can import our cards from the `data.js` file and iterate over them to show them all on the screen:

```jsx
import React from "react";
import "./App.css";

//Data
import cards from "./data"; /* 1 */

// Card Back Image
import cardBack from "../images/CardBack.jpg";

function App() {
  let cardsGrid = cards.map(card => {
    return (
      <div className="col-3 my-1">
        <img
          className="mx-auto"
          src={cardBack}
          height="100%"
          width="100%"
          key="back"
        />
      </div>
    );
  }); /* 2 */

  return (
    <div className="App border my-5">
      <div className="container">
        <div className="row">
          {cardsGrid} {/* 3 */}
        </div>
      </div>
    </div>
  );
}

export default App;
```

1. We import our array from `data.js` and store it as an array called `cards`
2. We iterate over the `cards` array using `.map` and return a `div` for every card. We store this array of divs in an array called `cardsGrid`
3. We use `cardsGrid` in our `JSX` code to render all the cards. By using Bootstrap's `row` and `col-3` classes the cards will appear in a grid

---

### Demo

You should now have a grid of face-down cards with all cards from your `data.js` file

![Grid of cards](https://imgur.com/1Sd7uyZ.png)

---

### Github

```shell
$ git add .
$ git commit -m "Show a grid of face-down cards"
$ git push
```

---

### Trello

This means you finished the card

> "As a player I will see a grid of cards (face down)"

Move the card from the `Doing` list to `Done`
