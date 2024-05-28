# CSS revert-layer keyword Explained
Maintaining a consistent design across various browsers and devices is an ongoing challenge in web development. This challenge includes adapting styles for different device screens and dealing with overridden styles due to conflicting specificity or inheritance hierarchies.

When encountering overridden styles, a common approach is to use the `!important` property, which gives a style priority over others. However, as CSS continues to evolve, more advanced solutions are being introduced to tackle these challenges. CSS cascade layers are emerging as a promising solution, providing a more refined approach to managing and resolving styles.

In this article, we will discuss CSS cascade layers, focusing on the `revert-layer` keyword. We will explain how the cascade layers function, when to utilize them, the purpose of the `revert-layer` keyword, and its various use cases.
## Exploring CSS Cascade Layers
The at-rule introduced by cascade layers belonging to `@layer` is particularly useful when dealing with multiple CSS sources. It allows authors to define and order their CSS rules or layering schemes, thereby avoiding specificity conflicts.

Cascade layers are especially beneficial when you are considering using the `!important` property in your CSS styles. They are highly relevant in such situations. Another scenario where cascade layers should be used is when there are conflicting CSS selectors and specificity.

We will discuss additional use cases for cascade layers later. In the meantime, let’s examine an example. In the following code, we have two cascade layers accompanied by HTML markup:
```html
<body>
  <ul>
    <li class="item feature">
      Item one
    </li>
    <li class="item">
      Item two
    </li>
    <li class="item">
      Item three
    </li>
  </ul>
</body>
```
The code above defines an unordered list `<ul>` with three list items `<li>,` each having the class `item.` The first list item also has the class `feature,` displaying three items in a list format.
```css
@layer base, special;

@layer special {
    .feature {
        font-weight: bold;
    }
}

@layer base {
    .item {
        color: blue;
    }
}
```
This code organizes CSS styles into two layers, with the `base` layer setting the text color of elements with the class `.item` to blue, and the `special` layer setting the font weight of elements with the class `.feature` to bold.

Similarly, we have arranged the layers in such a way that priority is given to the `special` layer over the `base` layer, resulting in the image shown below:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6032cdcc29f7beb140ba0ceb39363a44.png)
We can utilize multiple CSS sources or layers, allowing us to prioritize and override specific styles without relying on selector specificity or the `!important` property. 

In this article, our focus is on understanding the cascade layer keyword known as `revert-layer` and exploring its various use cases. Without further ado, let’s delve into the `revert-layer` CSS keyword
## Understanding CSS revert-layer
The `revert-layer` keyword in CSS allows a property to revert to the value of the same property in a previous layer of the cascade. If there is no previous value set, it reverts to the default browser styles. This keyword can be applied to any CSS property, including the shorthand property `all`. Here's an example:
```html
<body>
  <h1>Test Subject</h1>
  <ul>
    <li class="item feature">
      Subject one
    </li>
    <li class="item">
      Subject two
    </li>
    <li class="item">
      Subject three
    </li>
  </ul>
</body>
```
In the code above, we have a heading element and a list of items. Now, let’s write our CSS:
```css
@layer base, special;

@layer special {
  .item {
    color: red;
  }
}

@layer base {
  .item {
    color: blue;
    font-weight: normal;
    font-size: 16px;
  }
  .feature {
    color: green;
  }
}
```
The code above defines two layers (`base` and `special`), where `special` sets the `.item` color to red, and `base` sets the `.item` color to blue, font weight to normal, font size to 16px, and `.feature` color to green, with `base` taking precedence over `special.`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f19beff9354de1e7e5955c879601cdd.png)
In our previous example, we have two layers. As we explained earlier, all items will appear in red because the `color` property inside the `special` layer scheme takes the highest priority.

If we reorder our layers to `@layer special, base,` just as written below:
```css
@layer special, base;

@layer base {
  .item {
    color: blue;
    font-weight: normal;
    font-size: 16px;
  }
  .feature {
    color: green;
  }
}

@layer special {
  .item {
    color: red;
  }
}
```
As a result of the change made in the code, all items will become blue, excluding the first item, which will be green, just like shown in the image below:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bf91cc8cee97abd4b69bf4801869c2fa.png)
To implement the `revert-layer` keyword, add the styles below:
```css
@layer base, special;

@layer special {
    .item {
        color: orange;
    }
    .feature {
        color: revert-layer;
    }
}

@layer base {
    .item {
        color: blue;
    }
    .feature {
        color: green;
    }
}
```
In our `special` layer, we set the color to the value of `revert-layer` in the selector for the `.feature` item.

This means that every other color in the list of items turns orange, while the `.feature` item becomes green. 

Below is an image of the result:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_73ca42752df53b1522068386b6194900.png)
Our layer order prioritizes `@layer special` over `@layer base`. This means that the styles in `@layer special` are processed before those in `@layer base`. In `@layer special`, the `color` property for the `.feature` selector is set to `revert-layer`. As a result, the `color` property for `.feature` reverts to the value from the previous layer, which in this case is `@layer base`. In `@layer base`, there is a matching selector `.feature` with the `color` property set to green, so this is the value that is applied.

Additionally, if we remove the `.feature` selector from `@layer base`, the item with the `.feature` class reverts to the default color of the browser, which is typically black. However, since the item also has the class `.item`, it takes the `color: blue` property from the `.item` class in the `@layer base.` This is shown in the image below:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_746c528d7aa6c035e497838e69a1617a.png)
On the other hand, if there’s no matching selector property, the style reverts or rolls back to the browser's default origin styles. Please refer to the following HTML:
```html
<ul>
  <li class="feature">
    Subject one
  </li>
  <li class="item">
    Subject two
  </li>
  <li class="item">
    Subject three
  </li>
</ul>
```
This code creates an unordered list with three list items, where the first item has the class `feature` and the second and third items have the class `item`.

Below we have the CSS:
```css
@layer base, special;

@layer special {
    .item {
        color: orange;
    }
    .feature {
        color: revert-layer;
    }
}

@layer base {
    .item {
        color: blue;
    }
}
```
The CSS code above defines two layers, `base` and `special`, where `special` sets `.item` color to orange and `.feature` color to `revert-layer`, causing it to revert to the `.feature` color in `base`, which sets `.item` color to blue.

Below is the result of our code:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_baecf9c8cd61d5fd48754a21540c5fbb.png)
## Practical Applications
We have learned about the `revert-layer` and how to use it. Now, let’s explore some scenarios where it can be useful. Although the `revert-layer` is not widely used yet, it offers unique advantages in specific situations.
### Implementing modular styling
Modular styling, in the context of the `revert-layer` keyword in CSS, offers a powerful way to manage and maintain styles across different layers of a web application. The `revert-layer` keyword allows developers to selectively roll back styles to the values set in previous layers, enhancing the flexibility and control of modular styling.

By using modular styling, styles are scoped to specific components or modules, which prevents conflicts and makes it easier to manage styles. With the use of layers, each module can have its own layer, and the `revert-layer` feature can help manage overrides in a controlled manner. 

Modular styling can be effectively implemented using the `revert-layer` keyword. Here's how:

First we write out our HTML code:
```html
<body>
  <p class="text">Modular Button</p>
    <button class="button">Submit</button>
</body>
```
This code creates a paragraph with the text "Modular Button" styled with the `text` class, followed by a "Submit" button styled with the `button` class.

Now we write out our CSS code
```css
@layer base, special;

@layer base {
    .button {
        background-color: purple;
        color: white;
        padding: 10px 30px;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
}

@layer special {
    .button {
        background-color: revert-layer;
        color: revert-layer;
        border: revert-layer;
        border-radius: revert-layer;
        cursor: revert-layer;
        padding: 8px 20px;
    }
}
```
This CSS code defines two layers, `base` and `special`, where the `base` layer sets the default styles for the `.button` class, and the `special` layer partially overrides these styles while using `revert-layer` to revert certain properties back to their values from the `base` layer.

Overall, we kept every other property and only changed the padding. The result was:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9d29ec421a64230c95e52088994ead47.png)
### Executing a full global style reset
If you have used the `revert` keyword, you are aware that it removes the styles applied in the specified style origin and returns the style to the default browser style.

To gain a better understanding of this use case, let's examine the difference between `revert` and `revert-layer` using the following examples.

First, here's how the `revert` keyword is used:
```html
<body>
  <ul>
    <li class="item feature">
      Item one
    </li>
    <li class="item">
      Item two
    </li>
    <li class="item">
      Item three
    </li>
  </ul>
</body>
```
The HTML code above creates an unordered list with three items. The first item has the class `feature` and the second and third items have the class `item`.
```css
@layer base, special;

@layer special {
    .item {
        color: red;
    }
    .feature {
        color: revert;
    }
}
@layer base {
    .item {
        color: blue;
    }
}
```
This CSS code defines two layers, `base` and `special`, where `special` sets `.item` color to red and `.feature` color to revert to its default, while `base` sets `.item` color to blue.

In this scenario, all the items will be red because the `.item` selector has a `color: red` property. However, the `.feature` selector, which takes priority due to specificity, will revert to its default color using the `revert` keyword. This keyword rolls the style back to the browser style, which is black by default in browsers. 

The `revert` keyword does not consider if there’s another layer with the same styling; it simply reverts the styles back to the browser origin. 

See the result of the code above in the image below:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_062bcb5131182ff101822122d1eddcaa.png)
Now, let's consider an example of using the `revert-layer` keyword.

We will just make use of the previous HTML code written earlier for this example:
```html
<body>
  <ul>
    <li class="item feature">
      Item one
    </li>
    <li class="item">
      Item two
    </li>
    <li class="item">
      Item three
    </li>
  </ul>
</body>
```
Just as explaineda earlier the code above creates an unordered list with three items, where the first item has the class `feature` and the second and third items have the class `item`.

Now we take a look at the css code below carrying the function of the `revert-layer`:
```css
@layer base, special;

@layer base {
    .item {
        color: blue;
    }
    .feature {
        color: blue; /* Base layer sets feature to blue */
    }
}

@layer special {
    .item {
        color: red;
    }
    .feature {
        color: revert-layer; /* Reverts to the base layer's color */
    }
}
```
The CSS code above defines two layers, `base` and `special`. In the `base` layer, the `.item` and `.feature` classes are styled blue. In the `special` layer, the `.item` class is styled red. When using the `revert-layer` keyword, the `.feature` item will be styled blue because it reverts the styles back to the previous layer, which, in our case, is the `base` layer where the item is styled blue. Here’s the result:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5699075fc38caf265e84fdd8e244a684.png)
Moving forward, let’s consider the following example to demonstrate how we can utilize `revert-layer` as a global reset:

First lets write out our HTML code:
```html
<body>
  <ul>
    <li class="item feature">
      Item one
    </li>
    <li class="item">
      Item two
    </li>
    <li class="item">
      Item three
    </li>
  </ul>
</body>
```
The code above shows an unordered list with three items, where the first item has the class `feature` and the second and third items have the class `item`.
```css
&,
* {
    all: revert;
}

@layer base, special;

@layer special {
    .item {
        color: red;
    }
    .feature {
        color: revert-layer;
    }
}

@layer base {
    .item {
        color: blue;
    }
}
```
This CSS code resets all elements to their default styles using `all: revert`, then defines two layers (`base` and `special`) where the `.item` class is styled blue in the `base` layer and red in the `special` layer, and the `.feature` class reverts to the `base` layer's blue color. The image below shows the result of the code above:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_29e1088451c520db55bc518361572672.png)
`Revert-layer`, however, is more useful as it restores the styles to their original state, making it a more relevant choice.
### Modifying styles across layers
We have observed that the `revert-layer` keyword can be utilized to revert to the previous default styles of the browser. Let's consider a situation where we need to introduce a new styling layer.

This scenario might arise in the context of a large and intricate code base where we aim to prevent styling conflicts and preserve the designs. In such a scenario, a practical and effective approach would involve relocating the current designs into a layer and then creating a new layer.

See the code below:

First we write out our HTML code just like the previous
```html
<body>
  <ul>
    <li class="item feature">
      Item one
    </li>
    <li class="item">
      Item two
    </li>
    <li class="item">
      Item three
    </li>
  </ul>
</body>
```
The HTML code above creates an unordered list with three items, assigning the class `feature` to the first item and the class `item` to the second and third items.

Now lets look into the css code:
```css
@layer oldStyles, newStyles;

@layer oldStyles {
    .item {
        color: green;
    }
    .feature {
        color: #464646;
    }
}

@layer newStyles {
    &,
    * {
        all: revert-layer;
    }
  
  /* ... new styles here */
    .feature {
        color: blue;
    }
}
```
This CSS code defines two layers, `oldStyles` and `newStyles`, where the `.item` and `.feature` classes are styled in `oldStyles` with green and dark gray colors, respectively. In the `newStyles` layer, all styles revert to the previous layer (`oldStyles`), but the `.feature` class is then specifically styled with a blue color. The result is shown below:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa12174d71bbf547f30ff2ecff91515c.png)
This strategy allows elements to retain their old styles if desired, as we revert to the previous style origin set by the developer. This could also be relevant for style management or version control.
## Assessing Browser Compatibility
CSS cascade layers, such as the `revert-layer` keyword, offer promising capabilities for CSS architecture. However, it’s crucial to consider browser compatibility. Additionally, `revert-layer` is not easily polyfillable, which complicates its adoption in projects targeting a wide range of browsers.

[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/revert-layer#browser_compatibility)'s documentation officially states that browser support for the `revert-layer` is limited.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_699001a9392ddc136f3d5b982d598f96.png)
But after testing it myself, I can confirm that the `revert-layer` keyword is compatible and supported across multiple browsers such as Chrome, Firefox, Opera, and Brave. It should also be supported in Safari.
## Conclusion
We have explored how the `revert-layer` functions and how to utilize it. Understanding the `revert-layer` and its potential use cases or applications can enable developers to effectively leverage their capabilities in projects where browser compatibility allows.