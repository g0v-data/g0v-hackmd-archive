Here's the content for the HackMD project:

Difference between @mixin and @extends in Sass

Sass provides two powerful directives, ⁠ @mixin ⁠ and ⁠ extends ⁠, to promote code reuse and modularity. While they share similarities, they serve distinct purposes.

@mixin

⁠ @mixin ⁠ defines a reusable block of styles that can be included in multiple selectors.

Use Cases:

1.⁠ ⁠Define a set of styles for a specific component.
2.⁠ ⁠Create a library of reusable UI components.

Code Example:

scss
@mixin button-styles {
  background-color: #4CAF50;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.button-primary {
  @include button-styles;
}

.button-secondary {
  @include button-styles;
  background-color: #FF9800;
}


@extends

⁠ @extends ⁠ allows a selector to inherit styles from another selector.

Use Cases:

1.⁠ ⁠Create a base class with common styles.
2.⁠ ⁠Extend base styles for specific variations.

Code Example:

scss
%button-base {
  background-color: #4CAF50;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.button-primary {
  @extend %button-base;
}

.button-secondary {
  @extend %button-base;
  background-color: #FF9800;
}


Key Differences:

•⁠  ⁠⁠ @mixin ⁠ includes styles, while ⁠ @extends ⁠ inherits styles.
•⁠  ⁠⁠ @mixin ⁠ creates a new block of styles, whereas ⁠ @extends ⁠ modifies existing styles.

---

Block, Element, Modifier (BEM) Methodology

BEM is a naming convention for CSS classes that promotes structure, readability, and maintainability.

Block:

A self-contained component (e.g., ⁠ .navbar ⁠).

Element:

A smaller part of a block (e.g., ⁠ .navbar-item ⁠).

Modifier:

A variation of a block or element (e.g., ⁠ .navbar--dark ⁠).

BEM Syntax:

⁠ block__element--modifier ⁠

Example:

<nav class="navbar">
  <ul class="navbar__list">
    <li class="navbar__item">Home</li>
    <li class="navbar__item">About</li>
  </ul>
</nav>



.navbar {
  background-color: #333;
  padding: 1em;
}

.navbar__list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.navbar__item {
  display: inline-block;
  margin-right: 20px;
}

.navbar--dark {
  background-color: #000;
}


By following BEM, developers can write more organized, scalable, and maintainable CSS code.
