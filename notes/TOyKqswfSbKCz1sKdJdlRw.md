# CSS revert-layer keyword Explained
Maintaining a consistent design across various browsers and devices is an ongoing challenge in web development. This challenge includes adapting styles for different device screens and dealing with overridden styles due to conflicting specificity or inheritance hierarchies.

When encountering overridden styles, a common approach is to use the `!important` property, which gives a style priority over others. However, as CSS continues to evolve, more advanced solutions are being introduced to tackle these challenges. CSS cascade layers are emerging as a promising solution, providing a more refined approach to manage and resolve styles.

In this article, we will discuss CSS cascade layers, focusing on the `revert-layer` keyword. We will explain how cascade layers function, when to utilize them, the purpose of the `revert-layer` keyword, and its various use cases.
## Exploring CSS Cascade Layers
The at-rule introduced by cascade layers, belonging to `@layer`, is particularly useful when dealing with multiple CSS sources. It allows authors to define and order their CSS rules or layering schemes, thereby avoiding specificity conflicts.

Cascade layers are especially beneficial when you are considering using the `!important` property in your CSS styles. They are highly relevant in such situations. Another scenario where cascade layers should be used is when there are conflicting CSS selectors and specificity.

We will discuss additional use cases for cascade layers later. In the meantime, let’s examine an example. In the following code, we have two cascade layers accompanied by HTML markup:
```html
<body>
    <ul>
        <li class="item feature">Item one</li>
        <li class="item">Item two</li>
        <li class="item">Item three</li>
    </ul>
</body>
```
The code above defines an unordered list `<ul>` with three list items `<li>`, each having the class `item`. The first list item also has the class `feature`, displaying three items in a list format.
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

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_482cf382d3acac8789ee059cb6ab0382.png)

We can utilize multiple CSS sources or layers, allowing us to prioritize and override specific styles without relying on selector specificity or the `!important` property. 

In this article, our focus is on understanding the cascade layer keyword known as `revert-layer` and exploring its various use cases. Without further ado, let’s delve into the `revert-layer` CSS keyword
## Understanding CSS revert-layer
The `revert-layer` keyword in CSS allows a property to revert to the value of the same property in a previous layer of the cascade. If there is no previous value set, it reverts to the default browser styles. This keyword can be applied to any CSS property, including the shorthand property `all`. Here's an example:
```html
<body>
    <h1>Test Subject</h1>
    <ul>
        <li class="item feature">Subject one</li>
        <li class="item">Subject two</li>
        <li class="item">Subject three</li>
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
The code above defines two layers (`base` and `special`), where `special` sets `.item` color to red, and `base` sets `.item` color to blue, font weight to normal, font size to 16px, and `.feature` color to green, with `base` taking precedence over `special`.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_563228b2460d10cc80db682bdecbfb73.png)


In our previous example, we have two layers. As we explained earlier, all items will appear in red because the `color` property inside the `special` layer scheme takes the highest priority.

If we reorder our layers to `@layer special, base;` just as written below:
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
As a result of the change made in the code all items will become blue, excluding the first item, which will be green, just like shown in the image below:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea6ba091200c32fce7d15e68a7d045fa.png)

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

This means that every other color in the list of items turns orange, while the `.feature` item becomes green. This is because it reverts to the matching property of the previous cascade layer, which we assigned as green. 

Below is an image of the result:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3f62ba19dd519abd491b5aa8cbf0beb0.png)

Our layer order prioritizes `@layer special` over `@layer base`. This means that the styles in `@layer special` are processed before those in `@layer base`. In `@layer special`, the `color` property for the `.feature` selector is set to `revert-layer`. As a result, the `color` property for `.feature` reverts to the value from the previous layer, which in this case is `@layer base`. In `@layer base`, there is a matching selector `.feature` with the `color` property set to green, so this is the value that is applied.

Additionally, if we remove the `.feature` selector from `@layer base`, the item with the `.feature` class reverts to the default color of the browser, which is typically black. However, since the item also has the class `.item`, it takes the `color: blue` property from the `.item` class in the `@layer base.` This is reflected in the image below:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ba6d21cfd0af7ede3dffca590b4be1f.png)

On the other hand, if there’s no matching selector property, the style reverts or rolls back to the browser default origin styles. Please refer to the following HTML:
```html
<ul>
    <li class="feature">Subject one</li>
    <li class="item">Subject two</li>
    <li class="item">Subject three</li>
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

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1caacba2b6a7f328e8399368451b00a7.png)
## Practical Applications
We have learned about the `revert-layer` and how to use it. Now, let’s explore some scenarios where it can be useful. Although the `revert-layer` is not widely used yet, it offers unique advantages in specific situations.
### Implementing modular styling
Modular styling, in the context of the `revert-layer` keyword in CSS, offers a powerful way to manage and maintain styles across different layers of a web application. The `revert-layer` keyword allows developers to selectively roll back styles to the values set in previous layers, enhancing the flexibility and control of modular styling.

By using modular styling, styles are scoped to specific components or modules, which prevents conflicts and makes it easier to manage styles. With the use of layers, each module can have its own layer, and the `revert-layer` feature can help manage overrides in a controlled manner. 

Modular styling can be effectively implemented using the `revert-layer` keyword. Here's how:

First we write out our HTML code
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

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e52738072f4b4b9d72f03d10dae68620.png)
### Executing a full global style reset
If you have used the `revert` keyword, you are aware that it removes the styles applied in the specified style origin and returns the style to the default browser style.

To gain a better understanding of this use case, let's examine the difference between `revert` and `revert-layer` using the following examples.

First, here's how the `revert` keyword is used:
```

```
### Modifying styles across layers

## Assessing Browser Compatibility
## Conclusion