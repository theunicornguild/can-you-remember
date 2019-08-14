### How to check the flipped cards?

We want to only flip two cards at a time, if they're equal keep them flipped otherwise un-flip them

This feature will include changes in both the `Game` component and the `Card` component
`Game.js`

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

  let flippedCards = [];
  const changeFlipped = anArray => {
    flippedCards = anArray;
  }; //1

  const unflipCards = (unflip1, unflip2) => {
    setTimeout(() => {
      unflip1(false);
      unflip2(false);
    }, 1000);
  }; //2

  const checkFlipped = flippedObject => {
    changeFlipped([...flippedCards, flippedObject]);

    if (flippedCards.length === 2) {
      if (flippedCards[0].id !== flippedCards[1].id) {
        unflipCards(flippedCards[0].changeFlip, flippedCards[1].changeFlip);
      }
      changeFlipped([]);
    }
  }; //3

  //Mapping through the array of cards and placing them in the card component
  const cardList = cards.map((card, idx) => (
    <Card key={`${card.id}-${idx}`} card={card} checkFlipped={checkFlipped} /> //4
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

1. We defined an array that will contain the flipped cards and a function that will change the value of this array, the reason we didn't create this as a state (useState) because this change frequently and when states are changed they re-render any child components which we don't want
2. We defined a function called `unflipCards` that takes two functions and it will call those two functions sending them the value false (these two functions will be coming from the cards that are flipped to unflip them), the reason we have a timeout is to give the player a chance to see the flipped cards so he can match them later with other cards incase the flip went wrong
3. This function `checkFlipped` takes a flippedObject, will change the value of the flipped cards array to store the flippedObject in it and then checks, if there are two cards flipped and they are not equal it will call the `unflipCards` function and pass it the unflip functions of every card ao that they get un-flipped, then it empties the array of flipped cards, if they're equal it'll just empty the array in `1`

Then change `Card.js` to the following :

```jsx
import React, { useState } from "react";
import cardBack from "../images/CardBack.jpg";
import ReactCardFlip from "react-card-flip";

const Card = ({ card, checkFlipped }) => {
  const [flipped, changeFlip] = useState(false);

  const handleFlip = () => {
    if (flipped !== true) {
      changeFlip(true);

      checkFlipped({ id: card.id, changeFlip: changeFlip });
    }
  }; //1
  return (
    <div className="col-3 my-1">
      <ReactCardFlip isFlipped={flipped} flipDirection="horizontal">
        <img
          className="mx-auto"
          src={cardBack}
          //   used percentages instead of pixels to be responsive with the screen size
          height="100%"
          width="100%"
          key="front"
          onClick={() => handleFlip()} //2
        />

        <img
          className="mx-auto"
          src={card.front}
          //   used percentages instead of pixels to be responsive with the screen size
          height="100%"
          width="100%"
          key="back"
          onClick={() => handleFlip()} //2
        />
      </ReactCardFlip>
    </div>
  );
};

export default Card;
```

If you noticed that now the card component is receiving two props, the `card` object and the `checkFlipped` function

1. We defined a function called `handleFlip` that checks if the card is not already flipped it will flip it by calling `changeFlip` and then calls `checkFlipped` passing it an object with the id of the card and the changeFlip function of the card
2. Then whenever the card is clicked the `handleFlip` function is called
