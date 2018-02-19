# Bootstrap: Overview

**Zhenguo Chen**

## Introduction

What it says in [Bootstrap website](https://v4-alpha.getbootstrap.com/getting-started/introduction/) is not a brag:

>Bootstrap is the world’s most popular framework for building responsive, mobile-first sites and applications. Inside you’ll find high quality HTML, CSS, and JavaScript to make starting any project easier than ever.

Bootstrap is an open source toolkit developed by Mark Otto and Jacob Thornton at Twitter for building responsive
web. It has lots of prebuilt components and powerful plugins built on jQuery. Before Bootstrap, there were many
libraries used for developing web interface, which brings a hugh amount of burden for websites maintenance. One 
remarkable feature of Bootstrap is its support for [responsive web design](https://en.wikipedia.org/wiki/Responsive_web_design).
That means the layouts of your web apps can adjust dynamically and looks good on **ANY** platform (desktop, tablet,
mobile phone).

## Bootstrap Grid System

Bootstrap builds the layouts using a [grid system](https://getbootstrap.com/docs/4.0/layout/grid/). This grid 
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

The grid columns should always add up to twelve for a row. Bootstrap grid system provides four classes: xs for
phones, sm for tablets, md for small laptops and lg for laptops and desktops. To present a table of content,
you should create rows which hold columns, then put the content within columns. Here is an example code for
this basic structure:

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

<div class="container">
  <div class="row">
    <div class="col-sm">
      One of three columns
    </div>
    <div class="col-sm">
      One of three columns
    </div>
    <div class="col-sm">
      One of three columns
    </div>
  </div>
</div>

The Bootstrap grid system has four classes:

xs (for phones - screens less than 768px wide)
sm (for tablets - screens equal to or greater than 768px wide)
md (for small laptops - screens equal to or greater than 992px wide)
lg (for laptops and desktops - screens equal to or greater than 1200px wide)


introduction - introduce what bootstrap is and what it is usually used for, who created it, why was it created.
so you can say bootrap was was created becaus of standrdization of web app, look briefly into the history of 
bootstrap and see why it's created. another thing you can mention about bootstap is it is responsive, which 
means yuor web app looks good on ANY platform, be it phone, tablet, etc

second paragraph - talk about what makes up boostrap, which is the grid system - read more about it here: 
https://getbootstrap.com/docs/4.0/layout/grid/ - explain how the grid system works, maybe give an example, 
you can put in pictures to show how the grid system works, in fact the documentationa lready has it

third paragraph - how to use bootstrap: write the steps of using bootstrap, give an exmaple of a simple html 
document with CSS and JS links. this apragraph will look like it's long cause you will be giving an example

fourth paragraph - show components of bootstrap, create a simple form using bootstrap, check out the exmaple 
here: https://getbootstrap.com/docs/4.0/components/forms/ - you decide for yourself what's the best way to do 
this

conclusion - summarize advantages of bootstrap, say it's a good boilerplate for web deisgners to start with, 
bootstrap is good for develoeprs who just want a presentable website that can be built in an hour. then give 
links to bootstrap reousces