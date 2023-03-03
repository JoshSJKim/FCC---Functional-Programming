# FCC---Functional-Programming

- In functional programming, code is organized into smaller functions that can be combined to build complex programs.

## Learn About Functional Programming

- Functional programming is a style of programming where solutions are simple, isolated functions, without any side effects outside of the function scope.
- INPUT -> PROCESS -> OUTPUT

- Functional programming is about:
  - Isolated functions - there is no dependence on the state of the program, which includes global variables that are subject to change
  - Pure functions - the same input always gives the same output
  - Functions with limited side effects - any changes, or mutations, to the state of the program outside the function are carefully controlled.

Example of functional programming

```js
const prepareTea = () => 'greenTea';

const getTea = (numOfCups) => {
    const teacups = [];

    for (let cups = 1; cups <= numOfCups; cups +=1) {
        const teaCup = prepareTea();
        teaCups.push(teaCup);
    }
    return teaCups;
};

const tea4TeamFCC = getTea(40); // This will return 40 'greenTea' in the array 'teaCups'
```

## Understand Functional Programming Terminology

- Callback function: is a function that is passed as an argument to another function
  - It is intended to be called when a certain event occurs or when the first function has finished executing.
  - In simple terms, a callback function is a way to specify what should happen next in a program.
  - When the initial function is done with its work, or an event occurs, it calls the callback function to let the program know what to do next.

```js
function downloadImage(url, callback) {
    // downloadImage takes a url and a callback function as its arguments
    // the code to download the image goes here
    // when the image is downloaded, call the callback function
    callback(image);
}

function displayImage(image) {
    // This is an example of a callback function.
    // It takes the downloaded image as its argument.
    // Code to display the image goes here.
}

// The above is the setup.

downloadImage("httpsL//example.com/image.jpg", displayImage);
    // Calling function downloadImage will download image from the specified url and execute the callback 'displayImage'
```

- First class function: is a function that can be treated like any other value, like numbers or strings.

  - The function can be:
    - Stored in a variable or data structure
    - Passed as an argument to a function (callback)
    - Returned as a value from a function

- First class functions allows ability to write more modular and reusable code.
- You can write small, concise functions that can be combined and reused in different ways without redundancy.

```js
function functionInFunction(func) {
    // takes a function as an argument and calls the function
    func();
}

function sayHello() {       // This function is defined separately.
    console.log("Hello World!");    // When called, it will display "Hello World!" in the console.
} // This is an example of first class function in use. It can be treated like a value and pass it around to other functions.

functionInFunction(sayHello); // when functionInFunction is called, it will call the function 'sayHello' and display "Hello World!" in the console.
```

- Higher order function: is a function that takes another function as an argument, or returns a function as its result.

```js
function multiplyBy(num) {
    return function(x) {
        return x * num;
    }
}

const double = multiplyBy(2);
const triple = multiplyBy(3);

// The above is the setup

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

- This took a while for it to sink in.
- Still not a 100% clear.
  
- function 'multiplyBy' takes 'num' as its argument.
- When called, it returns a new function that takes 'x' as its argument, which then multiplies the values of 'x' and 'num'
- by defining variables 'double' and 'triple' and assigning the function 'multiplyBy' with 2 and 3 as its arguments, respectively,
  - the return function is stored in the variables.
- So, when you call 'double(5)', you're actually calling the function that is returned from calling 'multiplyBy(2)'.
  - 'multiplyBy(2)' is called, which returns a new function that takes 'x' as its argument and multiplies it by 2.
  - The new function is stored in the 'double' variable.
  - 'double(5)' is called, which calls the function that was returned by 'multiplyBy(2)' with 5 as its argument.
  - The new function multiplies 5 and 2 to return 10.

- I need more time to wrap my head around this

## Understand the Hazards of Using Imperative Code

- Functional programming is a good habit to develop.
  - It keeps the code easy to manage.
  - Prevents unintended bugs and errors.
  - Functional programming is a form of declarative programming.
  - It means that you tell the computer what you want done by calling a method or a function.

- Imperative programming is a bit different.
  - It give the computer a set of statements to perform a task.
  - You need to write out all the statements in order to achieve the desired outcome.
  - This means that it's prone to errors in the code, such as 'off by one errors' and semantic errors.
  - You could even use 'splice' instead of 'slice' which will produce a very different outcome.

Following are some examples of known hazards of using imperative coding

- State complexity:
  - Imperative code often requires the programmer to keep track of the program's state.
  - It can become complex as the program grows in size and complexity.
  - This can make it difficult to debug and maintain the code over time.

- Race conditions:
  - In imperative code, multiple processes or threads may access and modify shared data simultaneously.
  - It could lead to race conditions and unpredictable behavior.

- Mutable data:
  - Imperative code often relies on mutable data.
  - It can lead to unintended side effects and make it difficult to reason about the behavior of the code.

- Code duplication:
  - Imperative code can be verbose and repetitive, leading to code duplication and increased maintenance overhead.

- Difficulty of optimization:
  - Imperative code can be difficult to optimize because it relies on explicit control flow and state management.
  - It can make it harder for compilers to optimize the code.

- Readability and understandability:
  - Imperative code can be difficult to read and understand.
  - This is particularly true for novice programmers who may struggle to follow the control flow and state changes in the code.

## Avoid Mutations and Side Effects Using Functional Programming

- One of the core principles of functional programming is not to change things.
- Changes lead to bugs and errors.
- If you don't change anything - objects, function arguments, or variables - you could prevent unexpected results.

- Changing/altering is called 'mutation' and the outcome of that 'mutation' is called 'side-effects'.
- A function, ideally, should be a pure function, meaning, it should not cause any side effects.

```js
let fixedValue = 4;
function incrementer() {

}
```

- Write a code so that it returns the value of the global variable (fixedValue) increased by 1.
- The result should not mutate the original global variable.

```js
function incrementer() {
    return fixedValue += 1; // This was my first response, out of instinct, based on what I know and understand so far.
}
```

```js
function incrementer() {
    let newValue = fixedValue;  // This was my second attempt. Trying not to mutate the original variable.
    return newValue += 1;       // Instinctively, declare a new variable and assign the original to it.
}                               // This worked, but this is imperative coding
```

```js
function incrementer() {
    return fixedValue + 1; // Simply add 1 to the original variable. It does not mutate it, and it achieves the task of the challenge.
}
```

- I realize that excess information input has clouded my mind.
- I guess that is the point of this exercise. Keep things simple. Understand the problem and the goal of the challenge.

## Pass Arguments to Avoid External Dependence in a function

- In the previous challenge, the global variable was not altered, as intended.
- But the function 'incrementer' would not work without the global variable 'fixedValue' being present in the function.
- Another principle of functional programming is to always declare your dependencies explicitly.
  - In other words, if a function depends on a variable or an object for the function to work,
  - pass that variable or object directly into the function as an argument.
- By doing so,
  - The function is easier to test
  - You know exactly what input the function takes
  - It won't depend on anything else in the code
  - It increases confidence in altering, removing, or adding new code because it would be clear what you can or cannot change
  - You can see the potential traps
  - The function would always produce the same output for the same set of inputs.

```js
let fixedValue = 4;

function incrementer(value) {   // pass an argument to the function. The name of the argument can be arbitrary.
    return value + 1;
}

let increasedValue = incrementer(fixedValue);
console.log(increasedValue);    // console will display 5
console.log(fixedValue);        // global variable 'fixedValue' is unaffected and console displays 4
```

## Refactor Global Variables Out of Functions

- Remember the two principles for functional programming discussed so far.
  - Do not alter variable or object
  - Declare function parameters

- Remember declaring a new variable to copy a global variable (for example ```let newArr = bookList```) will not make a 'copy' of the original array.
  - It will simply create a reference to the existing variable specified.
  - Any changes made to 'newArr' will also affect the global variable 'bookList'.

```js
// The global variable
const bookList = ["The Hound of the Baskervilles", "On The Electrodynamics of Moving Bodies", "Philosophiæ Naturalis Principia Mathematica", "Disquisitiones Arithmeticae"];

// Change code below this line
function add(bookName) {

  bookList.push(bookName);
  return bookList;
  
  // Change code above this line
}

// Change code below this line
function remove(bookName) {
  const book_index = bookList.indexOf(bookName);
  if (book_index >= 0) {

    bookList.splice(book_index, 1);
    return bookList;

    // Change code above this line
    }
}
```

- Rewrite the above code so that the global array 'bookList' is not mutated inside either function 'add' or 'remove'.

```js
// The global variable
const bookList = ["The Hound of the Baskervilles", "On The Electrodynamics of Moving Bodies", "Philosophiæ Naturalis Principia Mathematica", "Disquisitiones Arithmeticae"];

// Change code below this line
function add(list, bookName) {      // add parameters to function to receive an array and a bookName
  let addedArr = list.slice(0);     // Use .slice(0) to copy the 'list' passed to the function.
  addedArr.push(bookName);          // spread operator [...list] would also work
  return addedArr;
  
  // Change code above this line
}

// Change code below this line
function remove(list, bookName) {
  let removedArr = list.slice(0);   // spread operator [...list] would also work
  const book_index = removedArr.indexOf(bookName);  // you can simplify this. Remove this line of code.
  if (book_index >= 0) {                            // if (removedArr.indexOf(bookName) >= 0) {
                                                    //   removedArr.splice(removedArr.indexOf(bookName), 1);
    removedArr.splice(book_index, 1);               // remove this line of code
    return removedArr;
    // Change code above this line
    }
}

let addedList = add(bookList, "A Brief History of Time");
let removedList = remove(bookList, "The Hound of the Baskervilles");
console.log(bookList);      // global array 'bookList' is unaffected
console.log(addedList);     // "A Brief History of Time" added to the list
console.log(removedList);   // "The Hound of the Baskervilles" removed from list
```

## Use the map Method to Extract Data from an Array

- I am just getting used to using for loops, if statements and push methods to iterate through arrays to create new arrays.
- Now theres a ```map``` method.
  - It iterates over each item in an array and returns a new array containing the results of calling the callback function on each element
  - AND it does this WITHOUT mutating the original array.
- When the callback is used, it is passed three arguments
  - the first argument is the current element being processed
  - the second is the index of that element
  - the third is the array upon which the ```map``` method was called

Below is a simple example using only the first argument of the callback

```js
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const names = users.map(user => user.name);
// declare a new variable, which will return a new array 'names'
// apply the 'map' method on the 'users' array
// iterate through each object 'user' in the array and return the value of the 'name' property from each object
// return new array 'names'
console.log(names); // [ 'John', 'Amy', 'camperCat' ]
```

```js
// The global variable
const watchList = [
  {
    "Title": "Inception",
    "Year": "2010",
    "Rated": "PG-13",
    "Released": "16 Jul 2010",
    "Runtime": "148 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Christopher Nolan",
    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page, Tom Hardy",
    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
    "Language": "English, Japanese, French",
    "Country": "USA, UK",
    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.8",
    "imdbVotes": "1,446,708",
    "imdbID": "tt1375666",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Interstellar",
    "Year": "2014",
    "Rated": "PG-13",
    "Released": "07 Nov 2014",
    "Runtime": "169 min",
    "Genre": "Adventure, Drama, Sci-Fi",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan, Christopher Nolan",
    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
    "Language": "English",
    "Country": "USA, UK",
    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.6",
    "imdbVotes": "910,366",
    "imdbID": "tt0816692",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "The Dark Knight",
    "Year": "2008",
    "Rated": "PG-13",
    "Released": "18 Jul 2008",
    "Runtime": "152 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan (screenplay), Christopher Nolan (screenplay), Christopher Nolan (story), David S. Goyer (story), Bob Kane (characters)",
    "Actors": "Christian Bale, Heath Ledger, Aaron Eckhart, Michael Caine",
    "Plot": "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, the caped crusader must come to terms with one of the greatest psychological tests of his ability to fight injustice.",
    "Language": "English, Mandarin",
    "Country": "USA, UK",
    "Awards": "Won 2 Oscars. Another 146 wins & 142 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_SX300.jpg",
    "Metascore": "82",
    "imdbRating": "9.0",
    "imdbVotes": "1,652,832",
    "imdbID": "tt0468569",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Batman Begins",
    "Year": "2005",
    "Rated": "PG-13",
    "Released": "15 Jun 2005",
    "Runtime": "140 min",
    "Genre": "Action, Adventure",
    "Director": "Christopher Nolan",
    "Writer": "Bob Kane (characters), David S. Goyer (story), Christopher Nolan (screenplay), David S. Goyer (screenplay)",
    "Actors": "Christian Bale, Michael Caine, Liam Neeson, Katie Holmes",
    "Plot": "After training with his mentor, Batman begins his fight to free crime-ridden Gotham City from the corruption that Scarecrow and the League of Shadows have cast upon it.",
    "Language": "English, Urdu, Mandarin",
    "Country": "USA, UK",
    "Awards": "Nominated for 1 Oscar. Another 15 wins & 66 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BNTM3OTc0MzM2OV5BMl5BanBnXkFtZTYwNzUwMTI3._V1_SX300.jpg",
    "Metascore": "70",
    "imdbRating": "8.3",
    "imdbVotes": "972,584",
    "imdbID": "tt0372784",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Avatar",
    "Year": "2009",
    "Rated": "PG-13",
    "Released": "18 Dec 2009",
    "Runtime": "162 min",
    "Genre": "Action, Adventure, Fantasy",
    "Director": "James Cameron",
    "Writer": "James Cameron",
    "Actors": "Sam Worthington, Zoe Saldana, Sigourney Weaver, Stephen Lang",
    "Plot": "A paraplegic marine dispatched to the moon Pandora on a unique mission becomes torn between following his orders and protecting the world he feels is his home.",
    "Language": "English, Spanish",
    "Country": "USA, UK",
    "Awards": "Won 3 Oscars. Another 80 wins & 121 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_SX300.jpg",
    "Metascore": "83",
    "imdbRating": "7.9",
    "imdbVotes": "876,575",
    "imdbID": "tt0499549",
    "Type": "movie",
    "Response": "True"
  }
];

// Only change code below this line

const ratings = [];
for (let i = 0; i < watchList.length; i++) {
  ratings.push({title: watchList[i]["Title"], rating: watchList[i]["imdbRating"]});
}


// Only change code above this line

console.log(JSON.stringify(ratings));
```

- Return a new array with a "title" key and name of the film, and a "rating" key with the iMDB rating.
- The above code works, but it uses a for loop to achieve this.
- Use the 'map' method on the watchList array to assign a new array object to the 'ratings' variable.

```js
const ratings = watchList.map(movies => ({ // declare a new variable that will return a new array 'ratings'
                                           // use 'map' method on the 'watchList' array and iterate through each object 'movies'
  "title": movies["Title"],                // return "title" key with the value of "Title" property from each 'movies' object
  "rating": movies["imdbRatings"]          // return "rating" key  with the value of "imdbRating" property from each 'movies' object
}));

console.log(JSON.stringify(ratings));   // console will display an array the same length as the original, with the title and rating property and values
```

## Implement map on a Prototype

- ```Array.prototype.map()```, or simply ```map()``` returns an array of the same length as the one it was called on.
- It also doesn't mutate the original array, as long as its callback function doesn't.

- ```map``` is a pure function.
  - its output depends solely on its inputs.
  - It also takes another function as its argument.

- Create ```Array.prototype.myMap()```
- The objective is to re-create the behavior of ```Array.prototype.map()``` without using the built-in ```map()``` method
- Use a 'for' loop and access the array instance using ```this```

```js
Array.prototype.myMap = function(callback) {
  const newArray = [];
  for (let i = 0; i < this.length; i++) {
    newArray.push(callback(this[i]));
  }
  return newArray;
}
```

- The above was my initial solution.
  - myMap() is declared with a function, which takes another callback function as its argument
  - the result will be returned in a new Array 'newArray'
  - Use a 'for' loop to iterate through the array 'myMap' is called on.
  - push the result of the callback function implemented on the element 'this[i]' to 'newArray'.
  - Return 'newArray'
- This is fine, as long as the argument passed to the callback is a single argument and returns a result of manipulating that single argument
  
- But the ```map()``` method takes three arguments
  - the current element being processed
  - the index of that element
  - and the array upon which 'map' was called.
- ```myMap()``` needs to be capable of receiving the above three arguments
  - it needs to use the callback function argument to transform the original array elements to fit the ```map()``` behavior criteria
  - it needs to apply the callback function to EACH element of the array and return new array based on the result of the function, rather than simply looping over the array.

```js
Array.prototype.myMap = function(callback) {
  const newArray = [];
  for (let i = 0; i < this.length; i++) {
    const transformedElement = callback(this[i], i, this); // This line can be removed and inserted directly in to the 'push'
    newArray.push(transformedElement);                     // newArray.push(callback(this[i], i, this));
  }
  return newArray;
}
```
