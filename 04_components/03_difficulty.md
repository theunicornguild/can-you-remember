Now we want to create a component to allow the player to choose the difficulty

In your `Components` folder create a file named `Difficulty.js`

This component will contain a title and 3 buttons for the player to choose the difficulty from

Add the code below to your Diffculty component

```jsx
import React from "react";

const Difficulty = () => {
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
          >
            Easy 4x3
          </button>
        </div>
        <div>
          <button
            type="button"
            className="btn btn-warning mb-3"
          >
            Medium 4x4
          </button>
        </div>
        <div>
          <button
            type="button"
            className="btn btn-danger "
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

Nothing new here just for this component to get rendered you will have to import it in your `App.js` and place it in your return 

Like the `Home` component the buttons do nothing yet