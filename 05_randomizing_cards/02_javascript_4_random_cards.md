### What do we need?

Now that we have our card component ready to use we want to make the cards list dependent on the difficulty of the game and we want to duplicate the cards so that there is two of each

To start with this feature we will need the following

1. If the difficulty is easy, normal, or hard we want to use the first six,8 or all cards from the `data` file, duplicate it then shuffle
2. to shuffle we need to define a function that would shuffle an array
3. store the shuffled cards and send them as props to the `Cards` component

---

### How to randomize cards ?

Create a file called `utils.js` which is a javascript file that will contain any functions we will need to use to create the following behavior

In your `utils.js` file place the following code:

```javascript
export const shuffle = list => {
  var j, x, i;
  for (i = list.length - 1; i > 0; i--) {
    j = Math.floor(Math.random() * (i + 1));
    x = list[i];
    list[i] = list[j];
    list[j] = x;
  }
  return list;
};
```

This code will be called later on and we will pass it an array it will return the same array but shuffled.

Then in our `App.js` file place the following code :

```jsx
import React, { useState } from "react";

// Data
import allCards from "./data";

// Utils
import { shuffle } from "./utils";

// Components
import Card from "./Components/Card";

//CSS
import "./App.css";

const App = () => {
  const [cards, setCards] = useState(shuffle([...allCards, ...allCards])));


  const cardsGrid = cards.map((card, idx) => (
    <Card key={`${card.id}-${idx}`} card={card} />
  ));

  return (
    <div className="App border my-5">
      <div className="container">
        <div className="row">
          <div className="col-9">
            <div className="row border">{cardsGrid}</div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default App;
```

The code above will allow you to see a grid of cards, in rows of fours and you can flip cards (no checking if flipped cards are equal and you can flip more than two cards a time)

1. We defined a state with the initial value "easy" for now we will have to set the difficulty depending on the user choice
2. We set the cards state to a duplicate of the cards required shuffled
