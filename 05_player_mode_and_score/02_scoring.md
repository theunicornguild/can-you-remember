### Trello

Move the cards `As a player in Single Player mode i can see the number of failed attempts` and `As a player in multiplayer mode I can see my score` from the `IceBox` List to the `Doing` list

### Score Component

To add score we will need to use the mode in the `Game` component therefore we have to pass the `mode` as props from `App.js`

```jsx
if (difficulty) return <Game difficulty={difficulty} mode={mode} />;
```

In the `Game` component we have to define states to keep track of scores and player's turn in multiplayer mode and failed attempts in single player mode

```jsx
import React, { useState, useEffect } from "react";

// Data
import allCards from "../data";

// Utils
import { shuffle } from "./utils";

// Components
import Card from "./Card";
import Score from "./Score";

const Game = ({ mode, difficulty }) => {
  const [cards, setCards] = useState([]);
  //   const [flippedCards, changeFlipped] = useState([]);

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
  }, [difficulty]);

  //To Store player score and pass them
  const [score, setScore] = useState([0, 0]); //1

  //To know which player's turn it is
  const [playerTurn, setPlayerTurn] = useState(true); //2
  const [failedFlips, increaseFailed] = useState(0); //3

  let flippedCards = [];
  const changeFlipped = anArray => {
    flippedCards = anArray;
  };

  const unflipCards = (unflip1, unflip2) => {
    setTimeout(() => {
      unflip1(false);
      unflip2(false);
    }, 1000);
  };

  const checkFlipped = flippedObject => {
    changeFlipped([...flippedCards, flippedObject]);

    if (flippedCards.length === 2) {
      if (flippedCards[0].id !== flippedCards[1].id) {
        unflipCards(flippedCards[0].changeFlip, flippedCards[1].changeFlip);
        increaseFailed(failedFlips + 1); //4
        setPlayerTurn(!playerTurn); //5
      } else {
        if (mode === "multi") {
          if (playerTurn) {
            //6
            setScore([(score[0] += 1), score[1]]);
          } else {
            setScore([score[0], (score[1] += 1)]);
          }
        }
      }
      changeFlipped([]);
    }
  };

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
        <Score //7
          mode={mode}
          score={score}
          failedFlips={failedFlips}
          playerTurn={playerTurn}
        />
      </div>
    </div>
  );
};

export default Game;
```

1. An array that keeps the score for the first player in the first element of the array and the second player in the second
2. A boolean that indicates whether its the first player's turn (true) or second player's turn (false)
3. An integer that keeps record of failed attempts for single player mode
4. In the `checkFlipped` function if the flipped cards are not equivalent the failed flips state increases by 1
5. if the cards don't match the player's turn gets switched
6. if the cards match and its in multiplayer mode the score of the corresponding player increases
7. Score component that will show the score

In the `Score` component, `Score.js`:

```jsx

import React from "react";

// Components
const Score = ({ mode, score, failedFlips, playerTurn }) => {
  return ({mode==="multi"? {/*1*/}
   <div className="col-3 border">
      <h3>Score</h3>
      <table className="table table-responsive mx-auto">
        <thead>
          <tr>
            <th scope="col" className={playerTurn && "text-danger"}> {/*2*/}
              Player 1
            </th>
            <th scope="col" className={!playerTurn && "text-danger"}> {/*2*/}
              Player 2
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>{score[0]}</td>
            <td>{score[1]}</td>
          </tr>
        </tbody>
      </table>
    </div>:
     <div className="col-3 mt-3">
      <div>
        <h6>Failed Attempts: {failedFlips} </h6>
      </div>
    </div>
  })
};

export default Score;


```

1. The component checks for the mode so it shows scores if the mode is multiplayer and shows failed attempts if single
2. If its in multiplayer mode, depending on the player's turn the player's name will be red in the player's turn

### Trello

Move the cards `As a player in Single Player mode i can see the number of failed attempts` and `As a player in multiplayer mode I can see my score` from the `Doing` List to the `Done` list

### Git

```shell
$ git add .
$ git commit -m "Score showing"
$ git push
```

---
### Demo
Single Player Mode:
![Single Player failed attempts](https://imgur.com/AArTmYS.png)
Multi Player Mode:
![Multi player scoring](https://imgur.com/vKXM5Dr.png)
