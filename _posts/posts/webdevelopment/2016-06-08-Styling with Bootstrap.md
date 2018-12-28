---
layout: post
title:  "Styling with Bootstrap"
date:   2016-06-03 00:44:45 -0500
categories: post
tags: Web-development
---
# Basic styling with Bootstrap

**Including Bootstrap style in html**

* Bootstrap can be included in a pages style by including the following in its head material `<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">`

**The Bootstrap grid**

<center><img src="https://s3.amazonaws.com/codecademy-content/courses/make-a-website/img/grid.svg" style="width:600px"></center>
* The Bootsrap grid divides the current viewable space of an HTML page into 12 equally-sized columns
* Elements are positioned and sized in this grid according to how many of the 12 columns they occupy
* Bootstrap has many pre-defined classes
    * `container` initiates a segment of html that will adhere to the 12 column grid
    * `row` are individual rows within a container that have 12 columns worth of space
    * `column` are the content that occupy the columns of a row
    * `jumbotron` is a special class that spans the entire page area, not just the 12 column space

**Rows and columns**

* The bootstrap hierarchy is container > row > item
* The following code:

```
<header class="container" style="background-color:green">
  <div class="row" style="background-color:LightGrey">
    <h1 class="col-sm-4" style="background-color:lightblue">Row1-Object1</h1>
    <h1 class="col-sm-8" style="background-color:salmon">Row1-Object2</h1>
  </div>
  <div class="row">
    <h1 class="col-sm-12">Row2-Object1</h1>
  </div>
  <div class="row" style="background-color:Grey">
    <h1 class="col-sm-4" style="background-color:lightblue">Row3-Object1</h1>
    <h1 class="col-sm-8" style="background-color:salmon">Row3-Object2</h1>
  </div>
</header>
```
  generates the following output:
<html>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">
<body>
  <header class="container" style="background-color:green">
    <div class="row" style="background-color:LightGrey">
      <h1 class="col-sm-4" style="background-color:lightblue">Row1-Object1</h1>
      <h1 class="col-sm-8" style="background-color:salmon">Row1-Object2</h1>
    </div>
    <div class="row">
      <h1 class="col-sm-6" style="background-color:lightblue">Row3-Object1</h1>
      <h1 class="col-sm-6" style="background-color:salmon">Row3-Object2</h1>
    </div>
    <div class="row" style="background-color:Grey">
      <h1 class="col-sm-8" style="background-color:lightblue">Row3-Object1</h1>
      <h1 class="col-sm-4" style="background-color:salmon">Row3-Object2</h1>
    </div>
  </header>
</body>
</html>

* Container - all of the content is contained in a single container class
    * The background color of the container is green
* Rows - notice there are 3 rows
    * The first and last row have their own background colors
    * The second row has no background-color, so you can see the green background of the parent container showing through around the column items
* Columns - each row has two column items
    * With each row, Object1 has more proportional space
        * Achieved with `col-sm-4` --> `col-sm-6` --> `col-sm-8`
        * Object2's space decreases to keep the sum of column sizes equal to 12
    * Notice that even though the text doesn't take up the entire span of the specified column size, that space is still occupied by the column
    * Notice that the text doesn't take up the full height of the row

**Columns and viewing size**

* The Bootstrap grid system automatically scales to the viewing area of the browser window/device
* However, at a certain point, reducing the viewing area and maintaining all grid elements proportionally will shrink grid elements to an impractical scale
* Column sizes specify when elements in a row should be positioned horizontally instead of further scaling down the elements

||Extra small|Small|Medium|Large|
|---|---|---|---|---|
|Class|`.col-xs-`|`.col-sm-`|`.col-md-`|`.col-lg-`|
|Device|Smartphone|Tablet|Laptop/Desktop|Desktop|
|Behavior|Always horizontal|Horizontal until break|Horizontal until break|Horizontal until break|
|Minimum viewing area before break|None|750px|970px|1170px|
|Column width at viewing size|Auto|~62px|~81px|~97px|

* If a screen or browser window is smaller than the minimum viewing area of a size class, the objects in that row will be placed horizontally
    * Above this minimum size, the elements will be placed horizontally
* Note that the extra small class has no break point and will always scale with decreased viewing area
