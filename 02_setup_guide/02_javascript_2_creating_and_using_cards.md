In your project directory you should have a `src/data.js` file.

This file should contain an array of card objects with the images to show on those cards. This array is `export`ed at the end so you can `import` it into your project later on.

We will be importing a minimum of 10 different cards faces from the `src/images/` directory (you can add more cards later if you want to increase the difficulty of your game). Our images have an aspect ratio of 3:2 Height:Width (this is to avoid design complication later on in the project). You should also find a `CardBack.jpg` image that we will be using later for the back of all the cards.

```javascript
//Cards Images import from the folder `images`
import AppleCard from "./images/AppleCard.jpg";
import CareemCard from "./images/CareemCard.jpg";
import CiscoCard from "./images/CiscoCard.jpg";
import EbayCard from "./images/EbayCard.jpg";
import FacebookCard from "./images/FacebookCard.jpg";
import GoogleCard from "./images/GoogleCard.jpg";
import IntelCard from "./images/IntelCard.jpg";
import PaypalCard from "./images/PaypalCard.jpg";
import TwitterCard from "./images/TwitterCard.jpg";
import UberCard from "./images/UberCard.jpg";

//Defining a constant array named cards
const cards = [
  //Creating card object that have an `id` with a unique value and a `front` with one of the imported images
  {
    id: 1,
    front: AppleCard
  },
  {
    id: 2,
    front: CareemCard
  },
  {
    id: 3,
    front: CiscoCard
  },
  {
    id: 4,
    front: EbayCard
  },
  {
    id: 5,
    front: FacebookCard
  },
  {
    id: 6,
    front: GoogleCard
  },
  {
    id: 7,
    front: IntelCard
  },
  {
    id: 8,
    front: PaypalCard
  },
  {
    id: 9,
    front: TwitterCard
  },
  {
    id: 10,
    front: UberCard
  }
];

// Here we are exporting the array of cards so that we can import it in any component as needed
export default cards;

/******
 * All product and company names are trademarks™
 * or registered® trademarks of their respective holders.
 * Use of them does not imply any affiliation with or endorsement by them.
 ******
```

Now that you understand the `data.js` file you will be using it in your project.
