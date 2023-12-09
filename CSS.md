# CSS Combinators

There are four different combinators in CSS:

- descendant selector (space)
- child selector (>)
- adjacent sibling selector (+)
- general sibling selector (~)

## Descendant Selector

The descendant selector matches all elements that are descendants of a specified element.
The following example selects all `<p>` elements inside `<div>` elements:

```
div p {
  background-color: yellow;
}
```

## Child Selector (>)

The child selector selects all elements that are the direct children of a specified element.
The following example selects all `<p>` elements that are direct children of a `<div>` element:

```
div > p {
  background-color: yellow;
}
```

## Adjacent Sibling Selector (+)

The adjacent sibling selector is used to select an element that is directly after another specific element.
Sibling elements must have the same parent element, and "adjacent" means "immediately following".
The following example selects the first `<p>` element that are placed immediately after `<div>` elements:

```
div + p {
  background-color: yellow;
}
```

## General Sibling Selector (~)

The general sibling selector selects all elements that are next siblings of a specified element.
The following example selects all `<p>` elements that are next siblings of `<div>` elements:

```
div ~ p {
  background-color: yellow;
}
```

## What is typography in CSS ?
The CSS properties that allow you to define the color, size, spacing, and shape of text
