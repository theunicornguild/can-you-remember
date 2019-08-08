Now that we created the card from the back, when the card is clicked nothing happens...

This is because the clicking event is not handled therefore we will have to use two new features of react, events and states

### What is an event ? ###
To have an interactive website we need to have events such as clicking, double clicking, hovering, etc. To handle those events we need event handlers, which are functions that run when a certain event occurs.

### What is a state? ###
One of the super powers of React is updating elements on the screen without refreshing the page! In React, we can build a whole app in one page without refreshing it, how amazing is that?!

To do that we will be using a `useState`, which is an hook that contains a dynamic property. Every component can have multiple states.


Modify the code in `App.js` to look like the following code :
```jsx
import React from "react";
import "./App.css";

//Data
import cards from "./data";

// Card Back Image
import cardBack from "../images/CardBack.jpg";

function App() {
const [flipped, changeFlip] = useState(false); {/* 1 */}

  return (
    <div className="App border my-5">
    <div className="container">
      <div className="row">
        <div className="col-3 my-1"> 
            <img
          className="mx-auto" 
          src={flipped?card[0].front:cardBack} {/* 3 */}
          height="100%"
          width="100%"
          key="back"
          onClick={() => changeFlip(true)} {/* 2 */}
        />
        </div>
      </div>
    </div>
    </div>
  );
}

export default App;


```
As you can see we added a state and an event handler
1. The state `flipped`'s default value is false
2. Whenever the image element is clicked it calls the `changeFlip` function and passes it the new value of `flipped` which is `true`
3. Now that we have a state that indicates whether the card is flip or not, in the `src` attribute of the image we can place an if condition that shows the front of the first card in the data file if true and shows the back card if false.
