# jQuery: Overview

**Zhenguo Chen**

## Introduction

[JQuery](https://en.wikipedia.org/wiki/JQuery) is the most widely-used open-source JavaScript libraries for
web development. It can greatly simplifies the process of creating web applications which are highly interactive
and responsive. With jQuery, you can enjoy features, such as [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming))
, animations. What's more, jQuery abstracts away the browser-specific features which makes it work across 
almost all modern browsers. This make development more efficient since you don't need to worry about how to
make features work well for every individual browser. Compared with JavaScript, jQuery's syntax is more compact,
and easier to read and maintain.

JQuery can help you retrieve content from the page, and perform some manipulation on it, then update your web
pages. For example, jQuery has a great feature called selector which use [CSS](https://www.w3schools.com/css/)
syntax to find and retrieve page content. By supporting features like this, web developer can easily get used
to jQuery and focus on web development.

## Features

### 1. Selectors And Filters

[Selectors and filters](https://www.sitepoint.com/comprehensive-jquery-selectors/) are one of the most 
important concept in jQuery. They are used to extract information from web pages so that we can do some 
manipulation on web page elements.

1.1. Selectors use CSS to find the desired content in web pages. Let me demonstrate with some examples:

```
$("p").css("font-size", "30px");
$(".selectedStyle").css("font-size", "30px");
$("#content").css("font-size", "30px");
```
* In the first line of the example, we have `$("p").css("font-size", "30px")`, which will select all the `<p>` 
tag and return them as a list of objects so that you can operate. In this case, we select all the paragraphs
and set the font size to `30px`.

* In the second line of the example, we have `$(".selectedStyle").css("font-size", "30px")`, which will select 
all the items that have a CSS class named `selectedStyle` regardless of their tags.

* In the third line of the example, we have `$("#content").css("font-size", "30px")`, which will select the item
with a id name `content`.

1.2. Filters are used to refine the results return by selectors. With selector, we can select all the `<p>` tags.
What if we only want the first paragraph? Then, we can use filters.

```
$("p:first").css("font-size", "30px");
```

 This example differs from the previous one with `:first` after the `p`. It will select only the first paragraph
 in current web page. You can also have some more complicated filter using operators, such as `not` operator:
 
```
$("p:not(.selectedStyle)").css("font-size", "30px");
```

### 2. Event Handler

JQuery has a very straightforward way to [handle events](https://learn.jquery.com/events/handling-events/). 
You can use `on` to start listening for a event, and use `off` to stop listening. For example:

```
$( "#button" ).click(function() {
  alert( "Handler for .click() called." );
});
```

Assume we have a button with id `button`. The example above will listen to click event, and when the button is
clicked, our callback function will start handling the event.

### Animation

JQuery provides a set of [animation effects](https://www.w3schools.com/jquery/jquery_animate.asp) which can
polish your web application significantly. By using `animate()` method, you can create customized animations.

```
$("button").click(function(){
    $("div").animate({left: '100px'});
});
```

As we mentioned in previous section, we have a button listening to an event in the example above. In the
callback function, we use `animate` method to move `<div>` element left. It is convenient to use `animate`
method to create your own animations. By combining animation and event handling, you can make your web pages
more interactive and responsive.