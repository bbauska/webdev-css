# webdev-css
An evergreen CSS course and reference to level up your web styling expertise.
## Welcome to Learn CSS! #
This course breaks down the fundamentals of CSS into digestible, easy to understand pieces. Over the next few modules, you'll learn how the core aspects of CSS work and how to use them effectively in your projects. Use the menu pane by the "Learn CSS" logo to navigate the modules.

You'll learn CSS fundamentals like the box model, cascade and specificity, flexbox, grid and z-index. And, along with these fundamentals, you'll learn about functions, color types, gradients, logical properties and inheritance to make you a well-rounded front-end developer, ready to take on any user interface.

Each module is full of interactive demos and self-assessments for you to test your knowledge. In addition to learning through reading and demos, there is an accompanying podcast episode for each topic as another way to learn and continue expanding your knowledge.

This course is created for beginner and advanced CSS developers alike. You can go through the series from start to finish to get a general understanding of CSS from top to bottom, or you can use it as a reference for specific styling subjects. For those new to web development overall, check out Learn HTML to learn all about how to write markup and link your stylesheets.

### Here's what you'll learn:

  - Box Model - Everything displayed by CSS is a box. Understanding how the CSS Box Model works is therefore a core foundation of CSS.
  - Selectors - To apply CSS to an element you need to select it. CSS provides you with a number of different ways to do this, and you can explore them in this module.
  - The cascade - Sometimes two or more competing CSS rules could apply to an element. In this module find out how the browser chooses which to use, and how to control this selection.
  - Specificity - This module takes a deeper look at specificity, a key part of the cascade.
  - Inheritance - Some CSS properties inherit if you don't specify a value for them. Find out how this works, and how to use it to your advantage in this module.
  - Color - There are several different ways to specify color in CSS. In this module we take a look at the most commonly used color values.
  - Sizing Units - In this module find out how to size elements using CSS, working with the flexible medium of the web.
  - Layout - An overview of the various layout methods you have to choose from when building a component or page layout.
  - Flexbox - Flexbox is a layout mechanism designed for laying out groups of items in one dimension. Learn how to use it in this module.
  - Grid - CSS Grid Layout provides a two dimensional layout system, controlling layout in rows and columns. In this module discover everything grid has to offer.
  - Logical Properties - Logical, flow relative properties and values are linked to the flow of text, rather than the physical shape of the screen. Learn how to take advantage of this newer approach to CSS.
  - Spacing - Find out how to select the best method of spacing elements, taking into consideration the layout method you are using and component that you need to build.
  - Pseudo-elements - A pseudo-element is like adding or targeting an extra element without having to add more HTML. They have a variety of roles and you can learn about them in this module.
  - Pseudo-classes - Pseudo-classes let you apply CSS based on state changes. This means that your design can react to user input such as an invalid email address.
  - Borders - A border provides a frame for your boxes. In this module find out how to change the size, style and color of borders using CSS.
  - Shadows - There are a number of ways to add shadows to text and elements in CSS. In this module you'll learn how to use each option, and the tasks they were designed for.
  - Focus - Understand the importance of focus in your web applications. You'll find out how to manage focus, and how to make sure the path through your page works for people using a mouse, and those using the keyboard to navigate.
  - Z-index and stacking contexts - In this module find out how to control the order in which things layer on top of each other, by using z-index and the stacking context.
  - Functions - CSS has a range of inbuilt functions. In this module you will find out about some of the key functions, and how to use them.
  - Gradients - In this module you will find out how to use the various types of gradients available in CSS. Gradients can be used to create a whole host of useful effects, without needing to create an image using a graphics application.
  - Animations - Animation is a great way to highlight interactive elements, and add interest and fun to your designs. In this module find out how to add and control animation effects with CSS.
  - Filters - Filters in CSS mean that you can apply effects you might only think possible in a graphics application. In this module, you can discover what is available.
  - Blend Modes - Create compositional effects by mixing two or more layers, and learn how to isolate an image with a white background in this module on blend modes.
  - Lists - A list, structurally, is composed of a list container element filled with list items. In this module, you'll learn how to style all the parts of a list.
  - Transitions - In this module, learn how to define transitions between states of an element. Use transitions to improve user experience by providing visual feedback to user interaction.
  - Overflow - Overflow is how you deal with content that doesn’t fit in a set parent size. In this module, you’ll think outside the box, and learn how to style overflowing content.
  - Backgrounds - In this module learn the ways you can style backgrounds of boxes using CSS.
  - Text and typography - In this module, learn how to style text on the web.
  - Conclusion and next steps - Further resources to help you take your next steps.
 
# 1. Box Model
Say you have this bit of HTML:
```[html]
<p>I am a paragraph of text that has a few words in it.</p>
```
Then you write this CSS for it:

```[css]
p {
  width: 100px;
  height: 50px;
  padding: 20px;
  border: 1px solid;
}
```

The content would break out of your element and it would be 142px wide, rather than 100px. Why is that? The box model is a core foundation of CSS and understanding how it works, how it is affected by other aspects of CSS and importantly, how you can control it will help you to write more predictable CSS.

https://codepen.io/web-dot-dev/pen/WNRemxN

A really important thing to remember when writing CSS, or working on the web as a whole, is that everything displayed by CSS is a box. Whether that's a box that uses border-radius to look like a circle, or even just some text: the key thing to remember is that it's all boxes.

Content and sizing #
Boxes have different behavior based on their display value, their set dimensions, and the content that lives within them. This content could be even more boxes—generated by child elements—or plain text content. Either way, this content will affect the size of the box by default.

You can control this by using extrinsic sizing, or, you can continue to let the browser make decisions for you based on the content size, using intrinsic sizing.

Let's quickly look at the difference, using a demo to help us.

```html
<main>
  <div class="wrapper">
    <article class="flow">
      <h1>Extrinsic sizing vs intrinsic sizing</h1>
      <figure class="callout">
        <p>
          Notice that when the box is using <strong>extrinsic sizing</strong>, there’s
          a limit of how much content you can add before it overflows out of the box’s
          bounds. This makes the word, “awesome”, overflow.
        </p>
      </figure>
      <label class="toggle" for="intrinsic-switch">
        <span class="toggle__label">Turn on intrinsic sizing</span>
        <input type="checkbox" role="switch" class="toggle__element" id="intrinsic-switch" />
        <div class="toggle__decor" aria-hidden="true">
          <div class="toggle__thumb"></div>
        </div>
      </label>
      <p class="awesome" data-element="awesome">CSS is awesome</p>
    </article>
  </div>
</main>
```

```css
.awesome {
  text-transform: uppercase;
  font-size: 5rem;
  font-weight: 700;
  line-height: 1;
  border: 5px solid;
  padding: 2rem;

  /* The important extrinsic width */
  width: 320px;
}

.awesome[data-sizing="intrinsic"] {
  width: min-content;
}
/*
Presentational styles 
*/
.awesome {
  --flow-space: 2rem;
}
```

```javascript
const awesome = document.querySelector('[data-element="awesome"]');
const intrinsicSwitch = document.querySelector("#intrinsic-switch");

// Set sizing attribute based on switch
intrinsicSwitch.addEventListener("change", () => {
  awesome.setAttribute(
    "data-sizing",
    intrinsicSwitch.checked ? "intrinsic" : "extrinsic"
  );
});
```

![image](https://github.com/bbauska/webdev-css/assets/41387907/8349146d-bf04-40bd-b2c3-8f79bf531dc3)


Notice that when the box is using extrinsic sizing, there's a limit of how much content you can add before it overflows out of the box's bounds. This makes the word, "awesome", overflow.

