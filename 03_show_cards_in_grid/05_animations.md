Now we want to add some animations to our cards so that they look like they are actually flipping

To do that we will use a library available online
If you used our `Starter File` ignore the yarn add

```shell
$ yarn add react-card-flip
```

Then in your `Card` Component import the library

```jsx
import React, { useState } from "react";
import cardBack from "../images/CardBack.jpg"; //1
import ReactCardFlip from "react-card-flip";

const Card = ({ card }) => {
  const [flipped, changeFlip] = useState(false);

  const handleFlip = () => { //2
    if (flipped !== true) {
      changeFlip(true);
        );
    }
  };
  return (
    <div className="col-3 my-1">
      <ReactCardFlip isFlipped={flipped} {/* 3 */} flipDirection="horizontal">
        <img
          className="mx-auto"
          src={cardBack}
          //   used percentages instead of pixels to be responsive with the screen size
          height="100%"
          width="100%"
          key="front"
          onClick={() => handleFlip()}
        />

        <img
          className="mx-auto"
          src={card.front}
          //   used percentages instead of pixels to be responsive with the screen size
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

1. Importing the library so we can use it within our component
2. We defined a function to flip the card only if its un-flipped otherwise do nothing- the reason we are going to use a function because we are going to do more than one thing whenever a card is flipped
3. As per the library's documentation, we have to put two images elements inside the `ReactCardFlip` and define the attribute `isFlipped` which should have a boolean value that indicates whether the card is flipped or not and the attribute `flipDirection` which takes the value horizontal or vertical depending on how you want the card to flip

You can find the documentation of this library [Here](https://www.npmjs.com/package/react-card-flip)

###Git

```shell
$ git add .
$ git commit -m "Added card animations"
$ git push
```
