## What is event capture and bubbling in Javascript ?

**Bubbling** and **Capturing** are the two phases of propagation. In their simplest definitions, bubbling travels from the target to the root, and capturing travels from the root to the target.

- The target is the DOM node on which you click, or trigger with any other event.
- The root is the highest-level parent of the target. This is usually the document, which is a parent of the , which is a (possibly distant) parent of your target element.

> **_In case of bubbling, event will propagate from the target and upto the root, watching for any event listeners._**

> **_In case of capturing, event will propagate from the root and upto the target, watching for any event listeners._**

example of bubbling :- Once you trigger the event, it will propagate up to the root, and it will trigger every single event handler which is associated with the same type. For example, if your button has a click event,during the bubbling phase, it will bubble up to the root, and trigger every click event along the way.

Order of event propagation :-

### Capture Phase -> Target Phase -> Bubbling Phase

Basically any event occurs, it propagates in this order, first in capturing phase, the event propagates from the parent element towards the target element,triggering all the event listeners defined in the capturing phase of the same type(click), then it triggers the event listener of the target element, then in bubbling phase,the event propagates(bubbles) towards the parent element from the target element triggering all the event listeners defined in the bubbling phase of the same type(click).

## What is Event.stopPropagation() ?

Calling **Event.stopPropagation()** will prevent further propagation through the DOM tree, and only run the event handler from which it was called. (from the target in bubbling phase).

```
function first() {
 console.log(1);
}
function second() {
 console.log(2);
}
var button = document.getElementById("button");
var container = document.getElementById("container");
button.addEventListener("click", first);
container.addEventListener("click", second);
```

In this example, clicking the button will cause the console to print 1, 2. If we wanted to modify this so that only the button’s click event is triggered, we could use Event.stopPropagation() to immediately stop the event from bubbling to its parent.

```
function first(event) {
  event.stopPropagation();
  console.log(1);
}
```

This modification will allow the console to print 1, but it will end the event chain right away, preventing it from reaching 2.

## What is the difference between **Event.stopPropagation()** and **Event.stopImmediatePropagation()** ?

**Event.stopPropagation()** will only stop propagation of all events leading upto all the parents. But it will not stop the events to be handled by more than 1 event handlers assigned to the same target element. Whereas **Event.stopImmediatePropagation()** will stop all the event handlers after the first event handler.

```
function first(event) {
  console.log(1);
}
function second() {
  console.log(2);
}
function third() {
  console.log(3);
}
var button = document.getElementById("button");
var container = document.getElementById("container");
button.addEventListener("click", first);
button.addEventListener("click", second);
container.addEventListener("click", third);
```

here we have two event handlers on the button, and clicking <div#container> will now print 3.

Adding **Event.stopPropagation()** to the first function, like so, will print 1, 2 to the console.

```
function first(event) {
  event.stopPropagation();
  console.log(1);
}
```

This is because **Event.stopPropagation()** will immediately prevent all click events on the parent from being triggered, but it does not stop any other event handlers from being called.

However, if you wanted to stop all event handlers after the first, that’s where **Event.stopImmediatePropagation()** comes in.

```
function first(event) {
  event.stopImmediatePropagation();
  console.log(1);
}
```

Now, the first function really will stop the parent click handlers, and all other click handlers. The console will now print just 1, whereas if we simply used **Event.stopPropagation(),** it would print 1, 2, and not including either would print 1, 2, 3 .

## How are event listeners for capture and bubbling phase created ? (code demonstration)

`document.addEventListener("click", handleClick);`

or

`document.addEventListener("click", handleClick,false);`

> above will create an event listener for the **bubbling** phase, where we either don't set the **third** argument or set it as **false**.

`document.addEventListener("click", handleClick,true);`

> above will create an event listener for the **capture** phase, where we set the **third** argument as **true**.

## How to sort array of strings alphabetically in Javascript ?

```
const data = ['t','A','a','B','b'];

data.sort((a,b) => {
return a.localeCompare(b);
})
```

above sorting function will give output as `['a','A','b','B','t']`

## Automatic Type Conversions

Automatic type conversions are performed by the Javascript interpreter to change data types of values based on the operators used in the Javascript expression.

```
let x = 5 + 7;       // x.valueOf() is 12,  typeof x is a number
let x = 5 + "7";     // x.valueOf() is 57,  typeof x is a string
let x = "5" + 7;     // x.valueOf() is 57,  typeof x is a string
let x = 5 - 7;       // x.valueOf() is -2,  typeof x is a number
let x = 5 - "7";     // x.valueOf() is -2,  typeof x is a number
let x = "5" - 7;     // x.valueOf() is -2,  typeof x is a number
let x = 5 - "x";     // x.valueOf() is NaN, typeof x is a number
```

## Difference between == and ===

The == comparison operator always converts (to matching types) before comparison. (**this comparison is also called loose comparison**)

The === operator forces comparison of values and type:

```
0 == "";        // true
1 == "1";       // true
1 == true;      // true

0 === "";       // false
1 === "1";      // false
1 === true;     // false
```

## What is call stack,callback queue and event loop ?

### Call stack

In a call stack, functions are added to the stack when called and removed when their execution is completed.

**_Note :- if a function is called and placed in the call stack, which in turn calls another function in its own execution, then that new function is placed on the call stack and so on(in case of infinite recursion it will lead to stack overflow as the call stack is finite)._**

### Callback queue

Callback queue basically contains all the asynchronous operations in a queue. While the statements are executed in the call stack if any asynchronous operation is encountered (setTimeOut or api call), it is added to the callback queue without blocking other statements. When the call stack becomes empty, that asynchronous operations gets executed in the stack.

In the callback queue, all asynchronous operations are lined up in the queue in a specific order, if the duration of all the operations are the same, then they will be executed sequentially i.e. the order in which they have been added to the queue.
But if each operation has different duration, then the operation having the smaller duration will get executed first, even if it is placed at the last(regardless of its position)

### Event loop

Basic function of the event loop is to check if the call stack is empty or not, if is empty, then it checks the callback queue for all the asynchronous operations whose duration is complete, and then places those operations in the call stack and executes them one by one (sequentially).

### What is hoisting in Javascript ?

Hoisting is a JavaScript behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can use a variable or function before it is declared in your code. However, it's important to note that only the declarations are hoisted, not the initializations or assignments.

Let's look at examples to understand hoisting with variables and functions:

#### 1. Variable Hoisting:

```
console.log(x);  // Outputs: undefined
var x = 5;
console.log(x);  // Outputs: 5
```

In the above example, the variable x is hoisted to the top of its scope during compilation, so the first console.log outputs undefined. The declaration var x is hoisted, but the assignment (x = 5) is not.

#### 2. Function Hoisting:

```
sayHello();  // Outputs: "Hello, World!"
function sayHello() {
  console.log("Hello, World!");
}
```

In this example, the function declaration function sayHello() is hoisted to the top of its scope, allowing you to call the function before its actual position in the code.

#### 3. Hoisting with let and const:

let and const declarations are also hoisted, but unlike var, they are not initialized with undefined until the point in the code where they are declared. This is known as the "temporal dead zone."

```
console.log(y);  // Throws a ReferenceError: y is not defined
let y = 10;
console.log(y);  // Outputs: 10
```

In this example, attempting to access the variable y before its declaration results in a ReferenceError.

#### 4. Function Expressions:

Function expressions, unlike function declarations, are not hoisted in the same way. The variable declaration is hoisted, but the assignment of the function expression is not.

```
sayHi();  // Throws a TypeError: sayHi is not a function
var sayHi = function() {
  console.log("Hi!");
};
```

In this case, the variable sayHi is hoisted, but it's not initialized with a function until the actual assignment statement is encountered during runtime.

## What is shallow copy and deep copy in Javascript ?

Both copies aim to duplicate object or array in a different object/array. The difference is that in
shallow copy, any changes made to the duplicate array, changes the original array also. Whereas, in
deep copy, any changes made to either of the array are independent of one another.

Example of shallow copy :-

```
let a = [1,2,3,4]
let b = a; // shallow copy
here if i change any index value of array b, it will array a also,
b[0] = -1;
console.log(b); // will print [-1,2,3,4]
console.log(a); // will print [-1,2,3,4]
```

Example of deep copy :-

```
let a = [1,2,3,4]
let b = JSON.parse(JSON.stringify(a)); // deep copy
here if i change any index value of array b,array a will remain unchanged,
b[0] = -1;
console.log(b); // will print [-1,2,3,4]
console.log(a); // will print [1,2,3,4]
```

Other ways of deep copy :-
`let b = strcuturedClone(a)`

Other ways of shallow copy :-

Spread Operator :- `let b = [...a]`;

Note :- Using spread operator will ensure that all the elements present at the 1st element are deep copied,
but any element which is nested will be shallow copied.
for example, below in case of nested, it will affect the original also:-

```
let a = [[0,1],2];
let b = [...a]; // shallow copy
b[0][0] = -1;
console.log(b); // will print [[-1,1],2]
console.log(a); // will print [[-1,1],2]
```

but if elements are present at first level only, then it will be a deep copy,

```
let a = [0,1,2];
let b = [...a]; // shallow copy
b[0] = -1;
console.log(b); // will print [0,1,2]
console.log(a); // will print [-1,1,2]
```
