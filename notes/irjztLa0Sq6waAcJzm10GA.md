# Difference Between @mixin and @extends in SASS and SCSS

# **@mixin**

**Definition: @mixin allow you to create a style that can be reused throughout your style sheet. You can pass parameter to @mixin and add the required value when you are calling it, Mixins are included into the current context using the @include at-rule, which is written as @include <name> or @include <name>(<arguments...>), with the name of the mixin being included.**

**Example:**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_51c3334e8d962007a0400fb34f92e854.png)

# @extends

**Definition: @extends allow one scss selector to inherit a style in another selector within the same style shit. it promote reuseability but its not as flexible as @mixin because it doesn't allow the use or agument or parameters which can promotes reuseability to another file. It’s open to errors from forgetting to include both classes, and it can bring non-semantic style concerns into your markup.**

**Example:**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1073b367db1f9bfdc77f8fa912e6a6de.png)


# Block, Element and, Modifier(BEM)

**BEM:This is a methodology that helps developer to create reusable components and code sharing in front‑end development and it also makes collaboration easier across teams.**

* *******Block*****: A block is a standalone component that is meaningful on its own. It can contain elements and modifiers.**

**Example: A header or card**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ecc523793f2bd08094ddbe146472e3b.png)

* ***Element:* An element is a part of a block that has no standalone meaning it's connected to its block. Elements are signified using double underscores.**

**Example: A header or card**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba811c39267ac060360c3ada1034634f.png)


***Modifier:*** **A modifier is a flag on a block or an element that changes its appearance or behavior. Modifiers are signified using double dashes.**

**Example: A header or card**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b96adc8ee8504732617af242e147bbe4.png)







