### What are components? ###
- Components are independent segments of code that split the user interface to manageable, cleaner, reusable pieces. You can think of them as custom HTML elements.

In other words components lets your code look cleaner, more understandable and halps you debug and trace your code easily incase of any errors 

### How do we create components ###
1. Create a new file of type `Filename.js`
   ```jsx 
   import React from "react";
   ```
2. Create a `function` which is our component (functional component)
3. The component’s name MUST begin with a capital letter.
4. The return value of this function is JSX elements that will be rendered on the screen.
5. Export the component’s function.

Below is an example of a `Functional Component` named `Home` 
```jsx
import React from "react";

function Home() {
    return (
        <h1>This is Home</h1>
    );
}

export default Home;
```