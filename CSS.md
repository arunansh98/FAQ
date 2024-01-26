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
