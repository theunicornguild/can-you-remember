In this component the player should be able to choose the mode (single or multiplayer) of which the player will be playing.

As you have seen in the live demo there was the title of the gamne and two buttons that show the different options

Create a folder in your project and name it`Components`
In your `Components` folder create a file named `Home.js` which will include your Home component's code

Place the code below in your `Home` Component

```jsx
import React from "react";

const Home = () => {
  return (
    {/*1*/}
    <div className="container">
    // 2
      <div className="jumbotron m-5">
        // 3
          <h1 className="mb-5">Can you remember?</h1>
        <div>
        // 4
          <button
            type="button"
            className="btn btn-warning mb-3"
          >
            Single Player
          </button>
        </div>
        <div>
        // 4
          <button
            type="button"
            className="btn btn-info"
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

1.   a div with the className `container`, containers are the most basic layout element in Bootstrap and are required when using our default grid system
2.   a `jumbotron` className is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.
3.   The className `mb-5` places a margin at the bottom of the heading so that whatever comes next doesnt be too close
4.   These two buttons are to choose the mode of the game but at the moment they dont do anything 

Now that you've created your Home page you can run your project by running the following command in the `shell`


```shell
yarn start
```

You will notice that nothing has changed in your project and the component you just created doesn't show

`React App` runs `App.js` so for you to run the `Home.js` component you will have to import it at the top of your `App.js` component then render it instead of what's already there 
look at the code bellow 

```jsx
import React from "react";
import "./App.css";

//Components
import Home from "./Components/Home";

function App() {
  return (
    <div className="App border my-5">
        <Home/>
    </div>
  );
}

export default App;

```

So as you can see we replaced everything with the `Home` component, now you will be able to see the Home component in your browser

### Git

Create a new checkpoint

```shell
$ git add .
$ git commit -m "DOne with static home component"
$ git push
```
___
