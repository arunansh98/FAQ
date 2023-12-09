## What is event capture and bubbling in Javascript ?

**Bubbling** and **Capturing** are the two phases of propagation. In their simplest definitions, bubbling travels from the target to the root, and capturing travels from the root to the target.

- The target is the DOM node on which you click, or trigger with any other event.
- The root is the highest-level parent of the target. This is usually the document, which is a parent of the , which is a (possibly distant) parent of your target element.

> **_In case of bubbling, event will propagate from the target and upto the root, watching for any event listeners._**

> **_In case of capturing, event will propagate from the root and upto the target, watching for any event listeners._**

example of bubbling :- Once you trigger the event, it will propagate up to the root, and it will trigger every single event handler which is associated with the same type. For example, if your button has a click event,during the bubbling phase, it will bubble up to the root, and trigger every click event along the way.

### Capture Phase -> Target Phase -> Bubbling Phase

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
