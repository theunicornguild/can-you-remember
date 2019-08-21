Now that we created our cards all facing down, when the card is clicked nothing happens...

This is because the clicking event is not handled therefore we will have to use two new features of react, events and states

### What is an event ?

To have an interactive website we need to have events such as clicking, double clicking, hovering, etc. To handle those events we need event handlers, which are functions that run when a certain event occurs.

### What is a state?

One of the super powers of React is updating elements on the screen without refreshing the page! In React, we can build a whole app in one page without refreshing it, how amazing is that?!

To do that we will be using a `useState`, which is an hook that contains a dynamic property. Every component can have multiple states.

Modify the code in `App.js` to look like the following code :

### Trello

Move the card 'As a player I can click a card to flip it over' from the `Backlog` list to the `Doing` list

```jsx
import React, { useState } from "react";
import cardBack from "../images/CardBack.jpg";

const Card = ({ card, checkFlipped }) => {
  const [flipped, changeFlip] = useState(false);{/*1*/}

  const handleFlip = () => {
    if (flipped !== true) {
      changeFlip(true);

      checkFlipped({ id: card.id, changeFlip: changeFlip });
    }
  };
  return (
    <div className="col-3 my-1">
        <img
          className="mx-auto"
          src={flipped?card.front:cardBack} {/* 3 */}
          //   used percentages instead of pixels to be responsive with the screen size
          height="100%"
          width="100%"
          key="back"
          onClick={() => changeFlip(true)} {/* 2 */}
        />
    </div>
  );
};

export default Card;

```

As you can see we added a state and an event handler

1. The state `flipped`'s default value is false
2. Whenever the image element is clicked it calls the `changeFlip` function and passes it the new value of `flipped` which is `true`
3. Now that we have a state that indicates whether the card is flip or not, in the `src` attribute of the image we can place an if condition that shows the front of the first card in the data file if true and shows the back card if false.

### Trello

Move the card 'As a player I can click a card to flip it over' from the `Doing` list to the `Done` list

### Git

```shell
$ git add .
$ git commit -m "Cards can flip"
$ git push
```
