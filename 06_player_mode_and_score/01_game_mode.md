### Trello

- Move the card 'As a player I can choose between single and multiplayer mode' from the `Backlog` list to the `Doing` list

### Mode Component

To allow the player to choose between single and multiplayer mode we will do the following

Create a new component named `Home` in `Home.js` because this is the first thing the player will see when they visit the game
in `Home.js` :

```jsx
import React from "react";

const Home = ({ setMode }) => {
  return (
    <div className="container">
      <div className="jumbotron m-5">
        <h1 className="mb-5">Can you remember?</h1>
        <div>
          <button
            type="button"
            className="btn btn-warning mb-3"
            onClick={() => setMode("single")}
          >
            Single Player
          </button>
        </div>
        <div>
          <button
            type="button"
            className="btn btn-info"
            onClick={() => setMode("multi")}
          >
            Multi Player
          </button>
        </div>
      </div>
    </div>
  );
};

export default Home;
```

As you can see there is a function `setMode` received as props and is called whenever a button is pressed, this functions came from `App.js`

Your `App.js` file should look like this now

```jsx
import React, { useState } from "react";
import "./App.css";
import Home from "./Components/Home";
import Difficulty from "./Components/Difficulty";
import Game from "./Components/Game";

function App() {
  const [mode, setMode] = useState(null); //1
  const [difficulty, setDifficulty] = useState(null);

  const page = () => {
    if (difficulty) return <Game difficulty={difficulty} />;
    if (mode) return <Difficulty setDifficulty={setDifficulty} />;
    return <Home setMode={setMode} />;
  }; //2

  return (
    <div className="App border my-5">
      {page()} {/*3*/}
      <div className="row">
        <div className="col-3">
          <button
            className="btn btn-danger mb-3"
            onClick={() => {
              setMode(null);
              setDifficulty(null);
            }}
          >
            Reset
          </button>{" "}
          {/* 4 */}
        </div>
      </div>
    </div>
  );
}

export default App;
```

1. We defined a new state to store the mode of the game and the initial value of the mode is null
2. we created a function that will determine which component to get rendered depending on the states `difficulty` and `mode`, if there is a difficulty the `Game` component will be rendered, but there cant be a difficulty until the mode is set , thats what the next if statement does, if the value of mode is null, the `Home` component is rendered otherwise the difficulty component
3. We called the function we just created to render the suitable component
4. Then we added a button that will set all main states to null therefore this will reset the game and will take the player back to the `Home` component, this button will show on all pages because its placed in the main `App` component

### Trello

- Move the card 'As a player I can choose between single and multiplayer mode' from the `Doing` list to the `Done` list

### Git

```shell
$ git add .
$ git commit -m "Mode choice done"
$ git push
```
