Before we mark this feature as `Done` on Trello, let's add some animations to our cards so that they look like they are actually flipping. This will be much nicer for the user.

To do that we will use an animation library for React (**KHALID - remove the library from the starter repo so they have to install**):

```shell
$ yarn add react-card-flip
```

Now we can import and use this library in our `Card` Component:

```jsx
import React, { useState } from "react";
import ReactCardFlip from "react-card-flip"; /* 1 */

import cardBack from "../images/CardBack.jpg";

const Card = ({ card }) => {
  const [flipped, changeFlip] = useState(false);

  /* 3 */
  const handleFlip = () => {
    changeFlip(!flipped);
  };

  return (
    <div className="col-3 my-1">
      {/* 2 */}
      <ReactCardFlip isFlipped={flipped} flipDirection="horizontal">
        <img
          className="mx-auto"
          src={cardBack}
          height="100%"
          width="100%"
          key="front"
          onClick={() => handleFlip()}
        />
        <img
          className="mx-auto"
          src={card.front}
          height="100%"
          width="100%"
          key="back"
          onClick={() => handleFlip()}
        />
      </ReactCardFlip>
    </div>
  );
};

export default Card;
```

1. We import the `ReactCardFlip` component from the library so we can use it within our component
2. We move the card flipping event handler into a function. We do this so we don't end up writing the function twice - once for each image. This will help us later when this function becomes more complicated.
3. Based on `react-card-flip`'s [documentation](https://www.npmjs.com/package/react-card-flip), we have to put two images elements inside the `ReactCardFlip` component - the first image is the back of the card, the second image is the front. We also pass an `isFlipped` prop which should have a boolean value that indicates whether the card is flipped or not. Finally, the `flipDirection` prop takes the string `horizontal` because that's how we want the cards to flip.

---

### Demo

The flipping of your cards should now be much nicer for the user.

**KHALID ADD A GIF FOR THIS**

---

###Git

```shell
$ git add .
$ git commit -m "Added card animations"
$ git push
```

---

### Trello

You can now move the card

> 'As a player I can click a card to flip it over'

from the `Doing` list to the `Done` list
