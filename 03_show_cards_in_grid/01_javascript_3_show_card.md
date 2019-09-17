### Trello

Move the first card in the `Backlog` list which is "As a player I will see a grid of cards (face down)" to the `Doing` list

---

### Card

We will start by placing our card in our project

In `App.js` your code should look like the following:

```jsx
import React from "react";
import "./App.css";

//Data
import cards from "./data";

// Card Back Image
import cardBack from "../images/CardBack.jpg";

function App() {


  return (
    <div className="App border my-5">
    <div className="container">
      <div className="row"> {/* 1 */}
        <div className="col-3 my-1"> {/* 2 */}
            <img
          className="mx-auto" {/* 3 */}
          src={cardBack}
          //   used percentages instead of pixels to be responsive with the screen size
          height="100%"
          width="100%"
          key="back"
        />
        </div>
      </div>
    </div>
    </div>
  );
}

export default App;


```

1. We placed the class `row` from bootstrap to make sure the cards inside the div are placed on the same line
2. We gave the card div the class `col-3` and `my-1` so that we can only have `4` cards per row and with some space between every row
3. Then we gave our image the class `mx-auto` from bootstrap to center the image in the div

### Git

```shell
$ git add .
$ git commit -m "Game layout"
$ git push
```

---
### Demo
![Card Back](https://imgur.com/5ax1KAi.png)

