This page is to generate or find the cards you will be using throughout the project

If you are going to be creating or finding your own cards its preferable that your cards have the aspect ratio of 3:2 Height:Width (this is to avoid design complication later on in the project)
You will be needing minimum of 10 different card faces and 1 card back (you can add more cards later if you want to increase the difficulty of your game)

In your project's `src` directory, create a directory called `images`, this folder will contain the images of your cards (for now 10 front cards and 1 back)

Then create a javascript file called `data.js` which will contain the list of cards giving them an `id` to be able to compare cards later on in the project

In your `data.js` file you will define an array and export it to use it in your code later
Use the `code` below in your `data.js` file

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
```

Now that you have defined the `data` you will be using in your project you are ready to start coding your components

### Git

Create a new checkpoint

```shell
$ git add .
$ git commit -m "added images and data file to the project"
$ git push
```

---
