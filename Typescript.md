# Typescript Notes

Very good Article:
https://blog.logrocket.com/types-vs-interfaces-in-typescript/

## Enums

```typescript
let petOnSale = "chinchilla";
let ordersArray = [
  ["rat", 2],
  ["chinchilla", 1],
  ["hamster", 2],
  ["chinchilla", 50],
];

// Write your code below:
enum Pet {
  Hamster = "HAMSTER",
  Rat = "RAT",
  Chinchilla = "CHINCHILLA",
  Tarantula = "TARANTULA",
}

const petOnSaleTS: Pet = Pet.Chinchilla;

let ordersArrayTS: [Pet, number][] = [
  [Pet.Rat, 2],
  [Pet.Chinchilla, 1],
  [Pet.Hamster, 2],
  [Pet.Chinchilla, 50],
];

ordersArrayTS.push(["HAMSTER", 1]);
```

## Setting Objects and Arrays of Object Types:

### Function using Objects:

```typescript
function sayHappyBirthdayWithObject(personObject: {
  name: string;
  age: number;
  giftWish: string;
  success: boolean;
}) {
  let output = "";
  output += "Happy Birthday " + personObject.name + "! ";
  output += "You are now " + personObject.age + " years old! ";
  output +=
    "Your birthday wish was to receive " +
    personObject.giftWish +
    ". And guess what? You will ";
  if (!personObject.success) {
    output += "not ";
  }
  output += "receive it! \n";
  console.log(output);
}

let birthdayBabies: {
  name: string;
  age: number;
  giftWish: string;
  success: boolean;
}[] = [
  { name: "Liam", age: 0, giftWish: "karate skills", success: false },
  { name: "Olivia", age: 0, giftWish: "a bright future", success: true },
  { name: "Ava", age: 0, giftWish: "$0.25", success: true },
];
```

## Types vs Interfaces:

```typescript
interface Song {
  artistName: string;
}

interface Song {
  songName: string;
}

const song: Song = {
  artistName: "Freddie",
  songName: "The Chain",
};

// Typescript will merge both interfaces into one, however if a type is used this will cause a conflict.
// Interfaces can be extended also, whereas types cannot. Useful for reuse later if you plan to add fields or values to them. However to limit them with a ‘type’ can be beneficial if you never want the data to change.
```

## Examples of Generic Types:

```typescript
type Human = { name: string; job: string };
type Dog = { name: string; tailWagSpeed: number };

type Family<T> = {
  parents: [T, T];
  mate: T;
  children: T[];
};
//Do not change the code above this line.

//Provide type annotations for the variables below:
let theFamily: Family<number> = {
  parents: [3, 4],
  mate: 9,
  children: [5, 30, 121],
};

//Here we declare the variable someFamily, we are defining the type as ‘Family’ as referenced above, and then we are defining the type of the values inside the family Type.

let someFamily: Family<boolean> = {
  parents: [true, true],
  mate: false,
  children: [false, false, true, true],
};

let aFamily: Family<Human> = {
  parents: [
    { name: "Mom", job: "software engineer" },
    { name: "Dad", job: "coding engineer" },
  ],
  mate: { name: "Matesky", job: "engineering coder" },
  children: [{ name: "Babesky", job: "none" }],
};

let anotherFamily: Family<Dog> = {
  parents: [
    { name: "Momo", tailWagSpeed: 3 },
    { name: "Dado", tailWagSpeed: 100 },
  ],
  mate: { name: "Cheems", tailWagSpeed: 7 },
  children: [
    { name: "Puppin", tailWagSpeed: 0.001 },
    { name: "Puppenaut", tailWagSpeed: 0.0001 },
    { name: "Puppenator", tailWagSpeed: 0.01 },
  ],
};
```
