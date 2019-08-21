### Trello

- Move the card 'As a player I can choose a difficulty level' from the `Backlog` list to the `Doing` list

### Difficulty Component

To let the player choose between the difficulties we will create a Difficulty component sending it the `setDifficulty` function

This component will contain a title and 3 buttons for the player to choose the difficulty from

Add the code below to your Difficulty component

```jsx
import React from "react";

const Difficulty = ({ setDifficulty }) => {
  return (
    <div className="container">
      <div className="jumbotron m-5">
        <div className="">
          <h1>Choose the difficulty</h1>
        </div>
        <div>
          <button
            type="button"
            className="btn btn-success mb-3"
            onClick={() => setDifficulty("easy")} {/* Setting the difficulty to Easy*/}
          >
            Easy 4x3
          </button>
        </div>
        <div>
          <button
            type="button"
            className="btn btn-warning mb-3"
            onClick={() => setDifficulty("medium")} {/* Setting the difficulty to Medium */}
          >
            Medium 4x4
          </button>
        </div>
        <div>
          <button
            type="button"
            className="btn btn-danger "
            onClick={() => setDifficulty("hard")} {/* Setting the difficulty to hard */}
          >
            Hard 4x5
          </button>
        </div>
      </div>
    </div>
  );
};

export default Difficulty;
```

As you can see the function `setDifficulty` is received as props and whenever a button is clicked the function is called with the difficulty clicked

Now because App.js will be doing a lot of things we need to refactor some of the code, therefore we will create a new component called `Game` in `Game.js`

```jsx
import React, { useState, useEffect } from "react"; //new import

// Data
import allCards from "../data";

// Utils
import { shuffle } from "./utils";

// Components
import Card from "./Card";

const Game = ({ difficulty }) => {
  const [cards, setCards] = useState([]);

  //Used to duplicate the amount of cards since we need two of each and shuffle them using the function defined at the top
  useEffect(() => {
    let cards = allCards;
    switch (difficulty) {
      case "easy":
        cards = allCards.slice(0, 6);
        break;
      case "medium":
        cards = allCards.slice(0, 8);
        break;
      default:
        break;
    }
    setCards(() => shuffle([...cards, ...cards]));
  }, [difficulty]); //1

  //Mapping through the array of cards and placing them in the card component
  const cardList = cards.map((card, idx) => (
    <Card key={`${card.id}-${idx}`} card={card} checkFlipped={checkFlipped} />
  ));

  return (
    <div className="container">
      <div className="row">
        <div className=" col-9">
          <div className="row border">{cardList}</div>
        </div>
      </div>
    </div>
  );
};

export default Game;
```

You will notice a new import `useEffect`
use Effect is used to do certain actions when the components is being rendered, when the components gets rendered and when a specific specified variable changes

In our case when the components is being rendered the cards get set and shuffled then whenever the difficulty is changed the component gets re-rendered

With this new component made, your `App.js. will look like that:

```jsx
import React, { useState } from "react";
import "./App.css";
import Home from "./Components/Home";
import Difficulty from "./Components/Difficulty";
import Game from "./Components/Game";

function App() {
  const [difficulty, setDifficulty] = useState(null);

  return (
    <div className="App border my-5">
      {difficulty ? (
        <Game difficulty={difficulty} />
      ) : (
        <Difficulty setDifficulty={setDifficulty} />
      )}
    </div>
  );
}

export default App;
```

We changed the default value for the difficulty to be null so that in our code we can check if difficulty has a value it renders the game component we created earlier, if not it renders the Difficulty component

### Trello

- Move the card 'As a player I can choose a difficulty level' from the `Doing` list to the `Done` list

### Git

Create a new checkpoint

```shell
$ git add .
$ git commit -m "Done with Difficulty component"
$ git push
```

---
