# CSS Combinators

There are four different combinators in CSS:

- descendant combinator (space)
- child combinator (>)
- adjacent sibling combinator (+)
- general sibling combinator (~)

## Descendant Combinator

The descendant combinator matches all elements that are descendants of a specified element. The children don't need to be direct.
The following example selects all `<p>` elements inside `<div>` elements:

```
div p {
  background-color: yellow;
}
```

## Child Combinator (>)

The child combinator selects all elements that are the direct children of a specified element.
The following example selects all `<p>` elements that are direct children of a `<div>` element:

```
div > p {
  background-color: yellow;
}
```

## Adjacent Sibling Combinator (+)

The adjacent sibling ombinator is used to select an element that is directly after another specific element.
Sibling elements must have the same parent element, and "adjacent" means "immediately following".
The following example selects the first `<p>` element that are placed immediately after `<div>` elements:

```
div + p {
  background-color: yellow;
}
```

## General Sibling Combinator (~)

The general sibling combinator selects all elements that are next siblings of a specified element.
The following example selects all `<p>` elements that are next siblings of `<div>` elements:

```
div ~ p {
  background-color: yellow;
}
```

## What is typography in CSS ?

The CSS properties that allow you to define the color, size, spacing, and shape of text

## What are basic selectors and combinators in CSS ?

### Basic Selectors

Basic selectors in CSS target HTML elements directly. They are used to apply styles to specific elements on the page. Common basic selectors include:

- Type or element selector: Targets elements based on their type (e.g., div, p).
- Class selector: Targets elements with a specific class (e.g., .my-class).
- ID selector: Targets a specific element with a unique ID (e.g., #my-id).
- Attribute selector: Targets elements with a specific attribute (e.g., [attribute="value"]).

### Combinators

Combinators are used to define relationships between different elements, allowing you to target more specific elements based on their structure in the HTML document. Common combinators include:

- Descendant combinator ( ): Selects all elements that are descendants of a specified element.
- Child combinator (>): Selects all direct children of a specified element.
- Adjacent sibling combinator (+): Selects an element that is immediately preceded by a specified element.
- General sibling combinator (~): Selects all siblings of a specified element.

### What are pseudo selectors ?

Pseudo-selectors in CSS are special keywords that are used to select and style specific parts of an HTML document or elements based on certain criteria or states. They allow you to target elements in ways that can't be expressed with simple element selectors alone.

Here are some commonly used pseudo-selectors:

1.`:hover: Selects and styles an element when the mouse cursor is over it.`

#### CSS

```
a:hover {
  color: red;
}
```

2.`:active: Selects and styles an element that is being activated (usually, when clicked).`

#### CSS

```
button:active {
  background-color: #00ff00;
}
```

3.`:focus: Selects and styles an element that has focus (typically used with form elements).`

#### CSS

```
input:focus {
  border: 2px solid blue;
}
```

4.`:first-child: Selects and styles the first child of a parent element.`

This will check if the first child element of the parent, if it matches the type such as li below, it will select it otherwise it will not.

#### CSS

```
li:first-child {
  font-weight: bold;
}
```

5.`:last-child: Selects and styles the last child of a parent element.`

This will check if the last child element of the parent, if it matches the type such as li below, it will select it otherwise it will not.

#### CSS

```
li:last-child {
  color: #ff0000;
}
```

6.`:nth-child(n): Selects and styles the nth child of a parent element. The value of n can be a number, an expression, or the keyword even or odd.`

#### CSS

```
li:nth-child(2n) {
  background-color: #f2f2f2;
}
```

7.`:nth-of-type(n): Similar to :nth-child, but it only counts elements of the specified type.`

#### CSS

```
p:nth-of-type(odd) {
  color: #008000;
}
```

8.`:not(selector): Selects and styles elements that do not match the specified selector.`

#### CSS

```
input:not([type="text"]) {
  opacity: 0.5;
}
```

9.`:first-of-type: Selects and styles the first element of its type among siblings.`

It basically selects all the child elements which are a direct childs of their parents and of the type specified in the prefix.

### CSS

```
h2:first-of-type {
  font-size: 24px;
}
```

These are just a few examples of the many pseudo-selectors available in CSS. They provide a powerful way to apply styles based on various conditions or relationships between elements.

**_Note :- basic difference between nth child and nth-of-type is that nth child will count all the child elements while searching the element type, whereas nth-of-type will count only the child elements that are of the element type._**

### What are pseudo elements ?

Pseudo-elements in CSS are used to style a specific part of an element. Unlike pseudo-classes, which target states or relationships of an element (e.g., :hover, :first-child), pseudo-elements target and style a part of the element's content.

Here are some commonly used pseudo-elements:

1.`::before and ::after: These are used to insert content before and after the actual content of an element. They are often used to add decorative elements or generate additional content.`

CSS

```
p::before {
  content: "Start: ";
}

p::after {
  content: " :End";
}
```

2.`::first-line and ::first-letter: These pseudo-elements allow you to style the first line or the first letter of an element.`

CSS

```
p::first-line {
  font-weight: bold;
}

p::first-letter {
  font-size: 150%;
}
```

3.`::selection: This pseudo-element targets the portion of text that a user has highlighted or selected.`

CSS

```
::selection {
  background-color: yellow;
  color: black;
}
```

4.`::placeholder: This is used to style the placeholder text in input fields.`

CSS

```
input::placeholder {
  color: #999;
}
```

### What is specificity in CSS ?

In CSS, specificity is a set of rules that determines which styles are applied to an element when there are conflicting or overlapping styles. Specificity is crucial for understanding how browsers decide which styles to prioritize when multiple rules target the same element.

The specificity of a selector is calculated based on the following criteria, with higher values taking precedence:

1.`Inline Styles: Styles applied directly to an element using the style attribute have the highest specificity.
`

HTML

```
<div style="color: red;">This text is red.</div>
```

2.`ID Selectors: Selectors containing an ID have higher specificity.
`

CSS

```
#myElement {
  color: blue;
}
```

3.`Class Selectors, Attribute Selectors, and Pseudo-Classes: Selectors containing classes, attributes, or pseudo-classes have moderate specificity.
`

CSS

```
.myClass {
  font-size: 16px;
}

[type="text"] {
  border: 1px solid #ccc;
}

a:hover {
  text-decoration: underline;
}
```

4.`Element Type Selectors and Pseudo-Elements: Selectors containing element types or pseudo-elements have lower specificity.`

CSS

```
div {
  background-color: #f2f2f2;
}

p::first-line {
  font-weight: bold;
}
```

### What is inheritance in CSS ?

Inheritance in CSS is the mechanism by which certain properties of a parent element are passed down to its children. When a child element doesn't have a value specified for a particular property, it can inherit that value from its parent. This helps in creating a consistent and efficient styling system.

**_Note :- Not all CSS properties are inherited; whether a property is inherited depends on its default behavior. Some common inherited properties include font-family, font-size, color, line-height, and text-align. On the other hand, properties like border, margin, and padding are typically not inherited._**

Inheritance simplifies styling by allowing you to set global styles on parent elements, reducing the need to apply styles to each individual child element. However, it's important to be aware of which properties are inherited and which are not, as this can affect how styles are applied throughout the document.

### What is box model in CSS ?

The CSS box model is a fundamental concept that describes the layout and structure of elements on a web page. It defines how elements are rendered and how their content, padding, border, and margin are positioned and sized. Each HTML element can be seen as a rectangular box, and the box model provides a way to understand and control the dimensions of these boxes.

The CSS box model consists of the following components:

- Content: The actual content of the box, such as text, images, or other media.

- Padding: The space between the content and the inner edges of the box. Padding adds space inside the border.

- Border: A border surrounding the content and padding. The border is drawn around the padding (if any) and the content.

- Margin: The space between the border of the box and the adjacent elements. Margin clears an area outside the border.

```
+---------------------------+
|        Margin             |
| +-----------------------+ |
| |       Border          | |
| | +-------------------+ | |
| | |      Padding      | | |
| | | +---------------+ | | |
| | | |   Content     | | | |
| | | +---------------+ | | |
| | +-------------------+ | |
| +-----------------------+ |
+---------------------------+

```

When you apply styles to an element, you are essentially affecting these different parts of the box model. For example, setting padding: 10px; would add 10 pixels of space inside the border, and setting margin: 20px; would add 20 pixels of space outside the border.

Understanding the box model is crucial for creating well-designed and responsive layouts in web development. It allows you to control spacing, borders, and overall layout in a consistent manner across different elements on a webpage.

What is shadow DOM ?

The Shadow DOM (Document Object Model) is a web standard that provides encapsulation for HTML and CSS in order to isolate the structure and style of a component from the rest of the document. It is often used in conjunction with web components to create modular and reusable UI elements.

Here are key concepts related to the Shadow DOM:

- Encapsulation:

  The Shadow DOM allows you to encapsulate the internal implementation details of a component, preventing styles and scripts from leaking out and global styles from affecting the component's internals.

- Shadow Tree:

  Inside a Shadow DOM, there is a separate document tree called the "shadow tree" that encapsulates the structure and style of the component. This tree is separate from the main document tree.

- Shadow Host:

  The element to which the Shadow DOM is attached is called the "shadow host." It is the container for the shadow tree. The shadow host and its shadow tree together form a scoped DOM subtree.

- ShadowRoot:

  The interface representing the root of the shadow tree is called ShadowRoot. It provides methods to manipulate the shadow DOM, such as accessing its content and styles.

- Scoped Styles:

  Styles defined within the Shadow DOM are scoped to that specific Shadow DOM subtree. They do not leak out to the global styles and do not get affected by global styles.

- Isolation:

  Shadow DOM provides a level of isolation, allowing developers to build components with internal styling and structure that is less likely to be unintentionally affected by external styles.

Using the Shadow DOM is common when creating web components, which are custom, reusable HTML elements with encapsulated functionality and styling. Here's a basic example:

HTML

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shadow DOM Example</title>
</head>
<body>

  <!-- Shadow host -->
  <div id="myComponent"></div>

  <script>
    // Shadow host element
    const shadowHost = document.getElementById('myComponent');

    // Create a shadow DOM
    const shadowRoot = shadowHost.attachShadow({ mode: 'open' });

    // Create an element inside the shadow DOM
    const paragraph = document.createElement('p');
    paragraph.textContent = 'This is a shadow DOM paragraph.';

    // Append the element to the shadow DOM
    shadowRoot.appendChild(paragraph);
  </script>

</body>
</html>
```

In this example, the div with the ID myComponent serves as the shadow host, and a p element is created inside its shadow DOM. The styles and content of the p element are encapsulated within the shadow DOM.
