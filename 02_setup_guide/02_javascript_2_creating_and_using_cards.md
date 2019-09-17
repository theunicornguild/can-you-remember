This page is to generate or find the cards you will be using throughout the project

We designed our cards to have the aspect ratio of 3:2 Height:Width (this is to avoid design complication later on in the project)
We will be needing minimum of 10 different cards faces and 1 card back (you can add more cards later if you want to increase the difficulty of your game)

In the `data.js` file we defined an array for you and exported it to use it in your code later

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

//Defining a constant named cards
const cards = [
  //Creating objects of cards that has the key `id` with a unique value and a `front` key with the picture of one of the cards as a value
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

//“All product and company names are trademarks™
//or registered® trademarks of their respective holders.
//Use of them does not imply any affiliation with or endorsement by them.”
```

Now that you understand the `data` file you will be using it in your project.
