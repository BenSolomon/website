---
layout: post
title:  "Basic CSS notes"
date:   2016-06-03 00:44:45 -0500
categories: post
tags: Web-development
---

# Basic CSS notes

### CSS styling

**Specifying CSS**

* CSS can be specified in multiple ways
    * Inline - style info is provided in actual tags
      * `<p style="color:blue;">This is blue text</p>`
      * <p style="color:blue;">This is blue text</p>
    * Internal - all style info is provided in the head section of the same HTML doc to be styled

        ```
        <!DOCTYPE html>
        <html>
        <head>
        <style>
        body {background-color:lightgrey;}
        p    {color:blue;}
        </style>
        </head>
        <body>

        <p>This is a paragraph.</p>

        </body>
        </html>
        ```
        * <p style="color:blue">This is a paragraph.</p>
    * External - all style info is provided in an additional css file
        * A css file can be linked by placing `<link rel="stylesheet" type="text/css" hrek="location"/>` in `<head>` material

**Style rules**

* Basic rules follow the form:
  ```
  tag {
    property:value;
    ...
  }
  ```
  * e.g. to make all `<h1>` text red, place following in css file
  ```
  h1 {
    color: red
  }
  ```

**Basic font styling**

* `font-family: font, alt font, ...` can accept many named fonts
    * Alt fonts are used to specify a font in the case that a users system can render the primary font
    * Multiple alt fonts can be used
* `color: ` can be specified with color names (`red`), hex code (`#FF0000`), or rgb (`rgb(255,0,0)`)
* `font-size: ` can be specified at pixels (`60px`), relative to default browser size (`1.5rem`), or relative to parent element size (`0.75em`)
    * On most browsers, `1rem` = `16px`
    * If the parent element size was `20px`, a child element with size `0.5em` would have a font size of `10px`

**Class styling**

* Instead of applying a single style to all instances of a particular tag, collections of styles can be assigned to a `class` that can be applied to specific sections of HTML
* The general format of a class is:
```
.className {
  styleRule;
  ...
}
```
    * Example to create a class that will be used to apply a font color only to a header
    ```
    .header {
      color: #ffffff
    }
    ```
    * Invoke this style in the HTML file by
    ```
    <div class=header>
        <h1>Text</h1>
    </div>
    ```
    * The resulting text will have color `#ffffff` regardless of tag
* Multiple classes can be assigned to a single tag
    * All classes should be within a single set of quotation marks and separated by spaces

**Tag-specific class styling**

* Sometimes, you do not want a component of a particular class to apply to all possible tags
    * E.g. You might want `<h1>` elements in a class to be red, while all other text is blue
    * Can be achieved with:

      ```
      <!-- CSS file -->
      .example p {
        color: red
      }

      <!-- HTML file-->
      <div class="example">
          <p>red text</p>
      </div>
      ```
or

    ```
    <!-- CSS file -->
    p.example {
      color: red
    }

    <!-- HTML file-->
    <div>
        <p class="example">red text</p>
    </div>
    ```
    * `.className tag {...}` will be applied to any instance of the specified tag that has a PARENT element with the specified className
    * `tag.className {...}` will be applied to any instance of the specified tag that ITSELF has the specified className
        * This functions the same a simply `.className {...}` with the exception that it can only be successfully applied to instances of the specified tag
* May be better to give each style of a tag its own class, rather than making tag-specific exceptions
    * This results in longer tag attributes, but limits the amount of repeated code in the CSS file needed for every exception to a rule

**Psuedo-class selectors**

* Psuedo-class selectors are selectors that modify classes
* The `active` psuedo-class is a class that only applies to a class when it is actively clicked

```
<style>
.ex p {color:red; position: relative}
.ex p:active {top:5px}
</style>
<div class="ex"><p>I move down when clicked</p></div>
```
<style>
.ex1 p {color:red; position: relative}
.ex1 p:active {top:5px}
</style>
<div class="ex1"><p>I move down when clicked</p></div>
    * `position` sets whatever position <p> takes as relative, so that when a `top` position is applied to the active psuedo-class, it moves relative to its starting position

**Backgrounds**

* `background-image` can add an image as a background-image
* `background-size` determines how the image fills the background spaces

**ID selectors**

* ID selectors are similar to classes, in that they allow you to specify style to a particular element
* However, unlike classes, ID selectors **can be used only once**
* Therefore, ID selectors are useful for one-time exceptions to a class rule
* ID selectors are specified with the `#` symbol in the css info
    * E.g. the following code will produce red text, even though the class rule specifies blue text
    ```
    p {
      color: blue
    }
    #exception {
      color: red
    }

    <p id="exception">This text is really red</p>
    ```

**Page spacing**

* Sections of a rendered HTML page are oriented according to the "box model"
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/W3C_and_Internet_Explorer_box_models.svg/2000px-W3C_and_Internet_Explorer_box_models.svg.png" alt="The Box Model" style = "width:300px"/></center>


* Border can add a border of a given thickness, pattern, and color around content
    * Basic form is `border: thickness pattern color`
    * E.g `border: 5px solid #F00`

<center><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="border:5px solid #F00"></center>

* Padding adds space between content and its border
    * Basic form is `padding: top right bottom left`
    * A single padding value will be applied equally to all sides
    * Eg. `padding: 20px`

<center><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="border:5px solid #F00; padding: 20px "></center>

* Margin determines how much space is placed between the content:padding:boarder element and other elements
    * Basic form is `margin: top right bottom left`
    * A single margin value will be applied equally to all sides
    * Eg. `margin: 5rem` (notice distance from this line)

<center><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="border:5px solid #FFF; padding: 20px; margin: 5rem "></center>


**Alignment**

* `display: inline` allows sequential items to be placed horizontally
  ```
  <style>.ex li {display: inline}</style>
  <div style="border:1px solid #F00; padding:5px; width:250px">
    <p>Default</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
    </ul>
    <p>Inline</p>
    <ul class="ex">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
    </ul>
  </div>
  ```
    <style>.ex li {display: inline}</style>
    <div style="border:1px solid #F00; padding:5px; width:250px">
      <p>Default</p>
      <ul>
          <li>Item 1</li>
          <li>Item 2</li>
          <li>Item 3</li>
      </ul>
      <p>Inline</p>
      <ul class="ex">
          <li>Item 1</li>
          <li>Item 2</li>
          <li>Item 3</li>
      </ul>
    </div>
* The `float` style places on object directly on top of whatever element it would otherwise follow
  ```
  <style>.ex li {display: inline}</style>
  <div style="border:1px solid #F00; padding:5px; width:250px">
    <p>Default</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li><p style="float:right">Float</p>
        <li>Item 3</li>
    </ul>
    <p>Inline</p>
    <ul class="ex">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li><p style="float:right">Float</p>
    </ul>
  </div>
  ```
<style>.ex li {display: inline}</style>
<div style="border:1px solid #F00; padding:5px; width:250px">
  <p>Default</p>
  <ul>
      <li>Item 1</li>
      <li>Item 2</li><p style="float:right">Float</p>
      <li>Item 3</li>
  </ul>
  <p>Inline</p>
  <ul class="ex">
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li><p style="float:right">Float</p>
  </ul>
</div>

* The `flex` layout allows for even distribution of items within a container
    * Begin with the style `display: flex` in the parent items

    ```
    <div style="display:flex">
      <img>
      <img>
    </div
    ```
<div style="display:flex"><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="margin:1rem"><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="margin:1rem"></div>
    * The default setting is to distribute flex horizontally, but without further attributes, this can distribute elements off the pages
    * The additional style `flex-wrap: wrap` will wrap any off page elements to the next row
<div style="display:flex; flex-wrap:wrap"><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="margin:1rem"><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="margin:1rem"></div>
    * `justify-content: center` can align the wrapped flex elements to the center
<div style="display:flex; flex-wrap:wrap; justify-content:center"><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="margin:1rem"><img  src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-3/moss2.jpg" style="margin:1rem"></div>
    * `align items:` can help to align differently shaped elements
        * Options include `flex-start`, `flex-end`, `center`, `stretch`, `baseline`
  <center><img src="https://css-tricks.com/wp-content/uploads/2014/05/align-items.svg"></center>
