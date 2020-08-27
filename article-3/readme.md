# Why you should use TypeScript

**Table of contents**
1. [Introduction](#introduction)
2. [What is TypeScript](#what-is-typescript)
3. [Types and Interfaces](#types-and-interfaces)
4. [Functions](#functions)
5. [Conclusion](#conclusion)
6. [Sources](#sources)
# Why you should use TypeScript
## Introduction
Since I started developing in JavaScript 5 years ago I haven't had such a big epiphany as I had when I began using TypeScript. When I first saw what the code looked like, TypeScript seemed like it was overdoing it and would mean more typing for the developer. I couldn’t have been more wrong. Typescript makes your code more readable, more concise and less prone to errors. In this article I hope to show you those characteristics as well as the basics of writing TypeScript.

## What is TypeScript

TypeScript is an object-oriented programming language and extends JavaScript by adding types. All valid JavaScript code is also TypeScript code. It is a superset of JavaScript and contains all of its elements. 

When coding in TypeScript you use a .ts file that is converted into a .js file using the Typescript Compiler. This is done in the build phase of a project. So the code that goes live is plain JavaScript. What this means is that TypeScript works much like a developer tool, making your life easier and finding inconsistencies or bugs before you run your code.

But how does TypeScript do that?

## Types and Interfaces
The way Typescript makes your code more readable and less prone to errors is by using types and interfaces. Let’s look at some examples.

###Types
There are types for each of the different kinds of data: booleans, numbers, strings and arrays. By adding `:boolean` (or any other type) behind the declaration you tell typescript what type to expect.

**Boolean**
``` ts
let isDone: boolean = false; //no error
let isDone: boolean = “false”; // error
```
**Number**
``` ts
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let big: bigint = 100n;
```
**String**
``` ts
let color: string = "blue";
color = "red";
```
**Array**
With arrays you define what type of array to expect, like an array of numbers or strings
``` ts
let list: number[] = [1, 2, 3];
```

###Interfaces
Interfaces are used when defining objects. Objects usually consist of different keys that can have different types. So when handling big Objects with multiple types of data you really want to define them in order to have more control and better error checking during coding.

**Object**
``` ts
interface Person { // This is the interface 
   firstName:string; 
   lastName:string; 
   sayHi: ()=>string; 
} 

let customer: Person = { // Here you assign the interface to the Object Person 
   firstName: "Tom",
   lastName: "Hanks", 
   sayHi: ():string =>{return "Hi there"} 
} 
```

What these types and interfaces do is that you can, just by reading the code, see what the relationships between pieces of code are. This means that your code can be much easier understood by someone who hasn’t worked on it. And also makes it much more obvious, in the form of typescript errors, when you do something that you are not supposed to do like adding up strings instead of numbers.


## Functions
Functions are the bread and butter of JavaScript. So naturally TypeScript has found a way to make these better to understand and less error prone. Let's dive into some code!

Here we have two simple functions, one named and one anonymous.

``` ts
// Named function
function add(x, y) {
  return x + y;
}

// Anonymous function
let myAdd = function (x, y) {
  return x + y;
};
```

Let’s add types.
``` ts
function add(x: number, y: number): number {
  return x + y;
}

let myAdd = function (x: number, y: number): number {
  return x + y;
};
```
What you see here is that the parameters are given a type `add(x: number, y: number)`. But also the return type `: number`. Now these are really simple functions. Let's see what you can do with more complicated functions .

``` ts
interface Card { // The Card interface
  suit: string;
  card: number;
}

interface Deck { // The Deck interface
  suits: string[];
  cards: number[];
  createCardPicker(this: Deck): () => Card;
}

let deck: Deck = { // Deck interface assigned to deck
  suits: ["hearts", "spades", "clubs", "diamonds"],
  cards: Array(52),
  // NOTE: The function now explicitly specifies that its callee must be of type Deck
  createCardPicker: function (this: Deck) {
    return () => {
      let pickedCard = Math.floor(Math.random() * 52);
      let pickedSuit = Math.floor(pickedCard / 13);

      return { suit: this.suits[pickedSuit], card: pickedCard % 13 };
    };
  },
};

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);
```

In the above function there is little room for error because everything is specified by types and interfaces. So when you do pass the wrong parameter to the function you get a neat error message in your editor that says where it went wrong, what went wrong and what was expected.


## Conclusion
I hope you can see that by using Typescript you can make your code better in an earlier stage of development. There is a bit of a learning curve as is the case with almost all of the many tools, frameworks and features of JavaScript. But once you get used to the way TypeScript is written I think it really pays dividends. Also the use of TypeScript is not boolean. You can use certain aspects of it, compile your code and it will work like any JavaScript project. This helps developers who are new to TypeScript gradually improve their skill in it.

Here are some of the things to keep in mind when deciding whether or not to start using TypeScript:

TypeScript simplifies JavaScript code, making it easier to read and debug.
TypeScript is open source.
TypeScript provides highly productive development tools for JavaScript 
TypeScript gives you all the benefits of ES6, plus more productivity.
TypeScript can help you to avoid bugs that you commonly run into when writing JavaScript by type checking the code.
Powerful type system
TypeScript is nothing but JavaScript with some additional features.
TypeScript code can be compiled as per ES5 and ES6 standards to support the latest browser.
TypeScript will save you time (after you have gotten used to it).


## Sources
Sharma, A. (2019, October 1). Why You Should Use TypeScript for Developing Web Applications - DZone Web Dev. Dzone.Com. https://dzone.com/articles/what-is-typescript-and-why-use-it
https://www.typescriptlang.org/


