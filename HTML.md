# What is !DOCTYPE html?

It is used for specifying which version of HTML needs to be used for rendering content on the web page.
for the latest version which is HTML5, we dont' need to explicitly specify any version as below :-

`<!DOCTYPE html>`

but in versions earlier than HTML5, you needed to specify which version of HTML is to be used using some type of links. for example as below :-

`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`

>

# What are block and inline elements?

Block elements always start on a new line and take up the full width by default.
Inline elements does not start on a new line and it only takes up as much width as necessary.
for ex:-
`<div>` element is a block level element.
`<span>` element is an inline element whose width depends on the text it contains.

> Note :- if any new custom tag is created, it will by default be inline.

# What are tags and attributes in html?

`<div align="center">First line</div>`

here above,

`<div></div>` are tags for enclosing the content which will be showed for the div element
align="center", here align is an attribute, attributes are used for speciifying additional info about the elements.

# What is head and title in html?

head is an html tag `<head></head>` which contains metadata i.e. data about data to be displayed on the web page.
It is not displayed.
ex:- style,title,script,link etc.
title is an html tag <title></title> which is used for displaying the text on the tab that is created for the page.

# How to change icon which is displayed to the left of title (in the tab) ?

add below tag inside head of html

```
<link
      rel="icon"
      href="https://media.geeksforgeeks.org/wp-content/cdn-uploads/gfg_200X200.png"
      type="image/icon type"
/>
```

where href is the path of the icon

# What is the difference between flex and inline-flex ?

`display:flex` will define a container that will always be on a new line.
`display:inline-flex` will define a container that will be inline with the previous element/container.

# What is the difference betweem framework and library ?

The main distinction between a framework and a library is that a framework inverts program control.
It informs the developer of what they require. A library, however, does not.
Instead, a programmer calls the library when and where he needs it.

# How reduce function works in Javascript ?

```
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  initialValue,
);

console.log(sumWithInitial);
// Expected output: 10
```

> here if any initial value is provided, then that value will be placed in the accumulator and the 1st element of the array will also be evaluated. (**accumulator will be the initial value and currentValue will be the 1st element**).

> But if no initial value is provided, then the value for first element will be the element itself and the calculation will start from the 2nd element in the array, for which **current value** will be **2nd element** (as shown above) and **accumulator** will be the first element in the array (as no initial value is provided, it will be the 1st element itself)

# How to add borders to an HTML table ?

```
<style>
      th,
      td,
      table {
        border: 1px solid green;
        border-collapse: collapse;
      }
<style>

<body>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Title</th>
          <th>Desgination</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Arunansh</td>
          <td>Mr</td>
          <td>My Desgination</td>
        </tr>
      </tbody>
    </table>
</body>
```

_**here border-collapse will make sure that we don't have double borders.**_

it will generate borders as below :-

![Alt text](image-3.png)

# How to use image as a link?

```
    <a href="https://www.youtube.com/" style="color: #f00"
      ><img
        src="https://www.youtube.com/s/desktop/7ea5dfab/img/favicon_96x96.png"
    /></a>
```

# What are description lists ?

In description lists, each and every list element also contains some sort of description added to it. for ex:-

```
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```

this will give below output :-

![Alt text](image-2.png)

where **black hot drink, white cold drink** are descriptions for **Coffee and Milk** resepectively.

# What are semantic elements ?

A semantic element clearly describes its meaning to both the browser and the developer. Examples of non-semantic elements: `<div>` and `<span>` - Tells nothing about its content. Examples of semantic elements: `<form>` , `<table>` , and `<article>` - Clearly defines its content.

# HTML Web Storage Objects

HTML web storage provides two objects for storing data on the client:

**window.localStorage** - stores data with no expiration date

**window.sessionStorage** - stores data for one session (data is lost when the browser tab is closed)

# What is contains() in Javascript ?

The contains() method returns true if a node is a descendant of a node.

ex:-

```
<!DOCTYPE html>
<html>
<body>
<h1>The Element Object</h1>
<h2>The contains() Method</h2>

<div id="myDIV">
<p>
I am a p element inside "myDIV", and I have a <span id="mySPAN"><b>span</b></span> element inside of me.
</p>
</div>

<p>Does the div element contain a span element?</p>
<p id="demo"></p>

<script>
const span = document.getElementById("mySPAN");
let answer = document.getElementById("myDIV").contains(span);
document.getElementById("demo").innerHTML = answer;
</script>

</body>
</html>
```

# What are SPA and MPA ?

## Single Page Applications (SPAs):

### Loading:

SPA: Loads a single HTML page initially.
MPA: Loads separate HTML pages for each distinct section.

### Navigation:

SPA: Navigates between sections without full page reloads, providing a seamless user experience.
MPA: Requires full page reloads when navigating between different sections.

### Interactivity:

SPA: Uses dynamic updates to modify content on the same page based on user interactions.
MPA: Relies on full page reloads to display new content.

### Technology:

SPA: Often built using frontend frameworks/libraries like React, Angular, or Vue.js.
MPA: Typically uses a more traditional approach without heavy reliance on frontend frameworks.

### Resource Loading:

SPA: Loads resources (like data) on demand, improving initial load times.
MPA: Loads resources with each new page, potentially leading to longer initial load times.

## Multi-Page Applications (MPAs):

### SEO (Search Engine Optimization):

SPA: SEO can be a challenge due to the reliance on JavaScript for content rendering.
MPA: Generally better for SEO, as each page has its own URL and can be indexed separately.

### Complexity:

SPA: Can have a more modular and structured codebase, enhancing development and maintenance.
MPA: May have a simpler code structure for each page, but can become complex as the application grows.

### Page Structure:

SPA: Typically has a single HTML file with dynamic updates.
MPA: Consists of multiple HTML files, each representing a distinct page.

### User Experience:

SPA: Offers a more dynamic and responsive user experience.
MPA: May feel slower due to full page reloads but can have faster initial load times.

### Development Approach:

SPA: Supports a more modular and component-based development approach.
MPA: Might involve a more traditional, page-centric development approach.
