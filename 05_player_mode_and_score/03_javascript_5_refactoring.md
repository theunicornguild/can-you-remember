There are a lot of things going on in the score component, they can clearly be divided into two components, `SingleplayerScore` and `MultiplayerScore`

For the `SingleplayerScore` component:

```jsx
import React from "react";

const SingleplayerScore = ({ failedFlips }) => {
  return (
    <div className="col-3 mt-3">
      <div>
        <h6>Failed Attempts: {failedFlips} </h6>
      </div>
    </div>
  );
};

export default SingleplayerScore;
```

For the `MultiplayerScore` component:

```jsx
import React from "react";

const MultiplayerScore = ({ score, playerTurn }) => {
  return (
    <div className="col-3 border">
      <h3>Score</h3>
      <table className="table table-responsive mx-auto">
        <thead>
          <tr>
            <th scope="col" className={playerTurn && "text-danger"}>
              Player 1
            </th>
            <th scope="col" className={!playerTurn && "text-danger"}>
              Player 2
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>{score[0]}</td>
            <td>{score[1]}</td>
          </tr>
        </tbody>
      </table>
    </div>
  );
};

export default MultiplayerScore;
```

Then we have to modify the `Score` component as following:

```jsx
import React from "react";

// Components
import MultiplayerScore from "./MultiplayerScore";
import SingleplayerScore from "./SingleplayerScore";

const Score = ({ mode, score, failedFlips, playerTurn }) => {
  if (mode === "multi")
    return <MultiplayerScore score={score} playerTurn={playerTurn} />;
  return <SingleplayerScore failedFlips={failedFlips} />;
};

export default Score;
```

### Git

```shell
$ git add .
$ git commit -m "Score Component Refactored"
$ git push
```
