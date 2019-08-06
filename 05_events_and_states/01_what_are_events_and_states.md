### What is an event ? ###
To have an interactive website we need to have events such as clicking, double clicking, hovering, etc. To handle those events we need event handlers, which are functions that run when a certain event occurs.

for example look at the button below
```jsx
<button onClick={()=> console.log("Ouch!")}>
Press me
</button>
```

You will notice that there is an `onClick` event handler where it takes a function and whenever the button is clicked it prints `"Ouch"` to the console 

We will be using this throughout the project and we will go back to components we have created and handle button clicks to execute a specific function (just not yet)


### What is a state?###
One of the super powers of React is updating elements on the screen without refreshing the page! In React, we can build a whole app in one page without refreshing it, how amazing is that?!

To do that we will be using a `useState`, which is an hook that contains a dynamic property. Every component can have multiple states.

look at the example below
```jsx
//Import useState
import React, {useState} from 'react';

const Example = () => {
    //State
    const [counter,setCounter] = useState(0)
  return (
    <div>
      <h1>{counter}</h1>
      <button 
      onClick={()=> setCounter(counter+1)}>
      Increment
      </button>
    </div>
  );
};

export default Example;
```

to declare a state you define it as a constant and in an Array the first variable is the name of the state and the second variable is the name of the function that will reassign the state a new value
The default value is then set using `useState(default value)`

So as you have noticed we used a button in the example above and an event handler so whenever the button is clicked it calls the function that sets the state and new value is the current state value + 1

Lets apply this understanding 
to our project
