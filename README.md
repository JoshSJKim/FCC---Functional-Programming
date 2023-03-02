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
