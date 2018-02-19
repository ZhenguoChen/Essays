# Bootstrap: Overview

**Zhenguo Chen**

## Introduction

What it says in [Bootstrap website](https://v4-alpha.getbootstrap.com/getting-started/introduction/) is not a brag:

>Bootstrap is the world’s most popular framework for building responsive, mobile-first sites and applications. Inside you’ll find high quality HTML, CSS, and JavaScript to make starting any project easier than ever.

Bootstrap is an open source toolkit developed by Mark Otto and Jacob Thornton at Twitter for building responsive
webs. It has many prebuilt components and powerful plugins built on jQuery. Before Bootstrap, there are many
libraries used for developing web interfaces, which brings a huge amount of burden for websites maintenance. One 
remarkable feature of Bootstrap is its support for [responsive web design](https://en.wikipedia.org/wiki/Responsive_web_design).
This means the layout of your web apps can adjust dynamically and still looks good on **ANY** platform (desktop, tablet,
mobile phone).

## Bootstrap Grid System

Bootstrap builds the layout using a [grid system](https://getbootstrap.com/docs/4.0/layout/grid/). The grid 
system allows up to 12 columns across the page. You can group the columns together to create a wider column.
The grid system can be [visualized](https://www.w3schools.com/bootstrap/bootstrap_grid_system.asp) as below:


<div class="table-responsive">
<table class="grid" cellspacing="0">
<tbody><tr>
  <td>span 1</td>
  <td>span 1</td>  
  <td>span 1</td>
  <td>span 1</td>
  <td>span 1</td>  
  <td>span 1</td>
  <td>span 1</td>
  <td>span 1</td>  
  <td>span 1</td>
  <td>span 1</td>
  <td>span 1</td>  
  <td>span 1</td>
</tr>
<tr>
  <td colspan="4">&nbsp;span 4</td>
  <td colspan="4">&nbsp;span 4</td>  
  <td colspan="4">&nbsp;span 4</td>
</tr>
<tr>
  <td colspan="4">span 4</td>
  <td colspan="8">span 8</td>  
</tr>
<tr>
  <td colspan="6">span 6</td>
  <td colspan="6">span 6</td>  
</tr>
<tr>
  <td colspan="12">span 12</td>
</tr>
</tbody></table>
</div>

The grid columns should always add up to 12 in a row. Bootstrap grid system provides four classes: xs for
phones, sm for tablets, md for small laptops and lg for laptops and desktops. To present a table of content,
you should create rows which hold columns, then put the content within columns. Here is an example code for
this basic structure which generates 3 columns:

```html
<div class="container">
  <div class="row">
    <div class="col-sm">
      column 1
    </div>
    <div class="col-sm">
      column 2
    </div>
    <div class="col-sm">
      column 3
    </div>
  </div>
</div>
```

<div class="table-responsive">
<table class="grid" cellspacing="0">
<tbody>
<tr>
  <td colspan="4">&nbsp;Column 1</td>
  <td colspan="4">&nbsp;Column 2</td>  
  <td colspan="4">&nbsp;Column 3</td>
</tr>
</tbody></table>
</div>

## How to use Bootstrap

Basically, there are 3 steps to use Bootstrap:

1. Create a HTML file since Bootstrap uses HTML elements and CSS properties.
2. Load Bootstrap with [CDN](https://en.wikipedia.org/wiki/Content_delivery_network) using
`<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">`
and `<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>`.
3. Create a container to wrap contents using `.container` and `.container-fluid`.

Here is an example which will generate the web page below:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container">
  <h1>Bootstrap Example</h1>
</div>

</body>
</html>
```

<img src="./img/Bootstrap_Demo.png" width="400" height="400" />

## Conclusion

Bootstrap is a perfect boilerplate for web developers to start with. It is good for developers who just want 
a presentable website that can be built withinin an hour. There are so many things you can do with Bootstrap,
I merely scratched the surface of the features Bootstrap can provide. I have listed some of the resources here for 
anyone who is interested.

* [Bootstrap 4 From Scratch With 5 Projects](https://www.udemy.com/bootstrap-4-from-scratch-with-5-projects/?siteID=my9IzLo0578-ZNndfh.f66bdj_oDmXDfdg&LSNPUBID=my9IzLo0578)
* [Bootstrap 4 Essential Training](https://www.lynda.com/Bootstrap-tutorials/Bootstrap-4-Essential-Training/372545-2.html?utm_medium=affiliate&utm_source=CJ&utm_content=11926&utm_campaign=CD17318&bid=11926&AID=CD17318&AIDCJ=12316367&PIDCJ=8238032&SIDCJ=raj&subid1=8238032)
* [Bootstrap Tutorial For Beginners](https://www.youtube.com/playlist?list=PLS1QulWo1RIaBQ1DOYYiJz38edqH_zwM1)
