# **Difference Between @mixin and @extends in SASS and SCSS

# **@mixin**

**Definition: @mixin allow you to create a style that can be reused throughout your style sheet. You can pass parameter to @mixin and add the required value when you are calling it, Mixins are included into the current context using the @include at-rule, which is written as @include <name> or @include <name>(<arguments...>), with the name of the mixin being included.**

**Example:**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_51c3334e8d962007a0400fb34f92e854.png)

# @extends

**Definition: @extends allow one scss selector to inherit a style in another selector within the same style shit. it promote reuseability but its not as flexible as @mixin because it doesn't allow the use or agument or parameters which can promotes reuseability to another file. It’s open to errors from forgetting to include both classes, and it can bring non-semantic style concerns into your markup.**

**Example:**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1073b367db1f9bfdc77f8fa912e6a6de.png)


# Block, Element and, Modifier(BEM)

BEM:This is a methodology that helps developer to create reusable components and code sharing in front‑end development and it also makes collaboration easier across teams.

Block: A block is a standalone component that is meaningful on its own. It can contain elements and modifiers.

Example: A header or card


- UML diagrams
```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
Note left of Alice: Alice responds
Alice->Bob: Where have you been?
```
- Auto-generated Table of Content
[ToC]

> Leave in-line comments! [color=#3b75c6]

- Embed YouTube Videos

{%youtube PJuNmlE74BQ %}

> Put your cursor right behind an empty bracket {} :arrow_left: and see all your choices.

- And MORE ➜ [HackMD Tutorials](https://hackmd.io/c/tutorials)
