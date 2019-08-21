Now that we have one card ready we can iterate over all cards in the data file and show them all on the screen

look at the code below:

```jsx
import React from "react";
import "./App.css";

//Data
import cards from "./data";

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
  }); /* 1 */
  return (
    <div className="App border my-5">
      <div className="container">
        <div className="row">
          {cardsGrid} {/* 2 */}
        </div>
      </div>
    </div>
  );
}

export default App;
```

1. Iterating over the cards in the data file and creating a card div and storing it in an array called `cardsGrid`
2. Calling `cardsGrid` in your code to render the list

---

### Trello

Running the code above will you show you all cards in your data file face down (This means you finished the `Trello` board card you were doing)

- Move the card from the `Doing` list to `Done`

---

### Github

```shell
$ git add .
$ git commit -m "Can see a grid of cards"
$ git push
```