### Creating a Card and Grid Component

`App.js` is getting messy so to clean our code we are going to refactor the `cards` code to a separate component

### What is a component?

- Components are independent segments of code that split the user interface to manageable, cleaner, reusable pieces. You can think of them as custom HTML elements.

In other words components lets your code look cleaner, more understandable and helps you debug and trace your code easily incase of any errors

Create a folder in your project and name it`Components`
In your `Components` folder create a file named `Card.js` which will include your Card component's code

We will remove some code from the `App.js` component and add it to the `Card.js` component to look like the following :

`App.js`:

```jsx
import React from "react";
import "./App.css";

//Data
import cards from "./data";

// Card Back Image
import cardBack from "./images/CardBack.jpg";

//Components
import Card from "./Components/Card";

function App() {
  let cardsGrid = cards.map(card => <Card card={card} />); /* 1 */
  return (
    <div className="App border my-5">
      <div className="container">
        <div className="row">{cardsGrid}</div>
      </div>
    </div>
  );
}

export default App;
```

`Cards.js`:

```jsx
import React, { useState } from "react";
import cardBack from "../images/CardBack.jpg";
import ReactCardFlip from "react-card-flip";

const Card = ({ card }) => {
  /* 2 */
  const [flipped, changeFlip] = useState(false);

  return (
    <div className="col-3 my-1">
      <img
        className="mx-auto"
        src={cardBack}
        //   used percentages instead of pixels to be responsive with the screen size
        height="100%"
        width="100%"
        key="front"
      />
    </div>
  );
};

export default Card;
```

1. After we have imported the `Card` component, when calling it we have to pass `props`

### What are props?

Props are information that are passed between components
Those information can be data or functions

2. This is how we used props in our `Card` functional component by putting it as parameters

Now when you render your `App.js` The page will look exactly the same

Next : We're going to let the cards flip whenever they are clicked

###Git

```shell
$ git add .
$ git commit -m "Cards component refactor"
$ git push
```