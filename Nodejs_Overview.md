# Node.js Overview

**Zhenguo Chen**

## Introduction

As described in this awesome [tutorial](https://www.lynda.com/Node-js-tutorials/Up-Running-Node-js/370605-2.html):
>Node.js is and open-source cross platform runtime environment for server-side and networking
applications. It is built on top of Chrome's JavaScript runtime, the V8 engine. Also, 
applications for Node are written in JavaScript. This is why many developers like Node
because it'g lightweight and you can write your front-end and back-end in the same language.

It is usually confusing for beginner, what is the relationship between Node.js and 
JavaScript? From my understanding, Node.js is an interpreter and environment for 
JavaScript. It integrates lots of libraries for using JavaScript and focuses on 
asynchronicity and non-blocking operations. It is not itself a programming language.

## Asynchronous

One of the most important features for Node.js is its asynchronous operation which can
improve user experience dramatically. To understand asynchronous operation, let's compare 
with synchronous operation. For synchronous operation, to move on to the next task, we
need to wait until current task is finished and this results in blocking. On the other hand, for
asynchronous operation, we can move on to next task without waiting for current task to
finish. For example, we have a web page which need to read files from our system and this may
take some time. For synchronous operation, we need to wait until files are loaded, then
we can interact with users. With asynchronous operation, we can still interact with users
while we are reading files.

Here is a simple example for comparing asynchronous operation with synchronous operation:

```
// synchronous operation
fs = require('fs');

files = fs.readdirSync('./');
console.log('files:', files);

console.log('users are waiting');

----------------------------
output:
files: [ '.idea', 'HelloWorld.html', 'async-demo.js', 'sync-demo.js' ]
users are waiting
```

The output may be different depending on what you have in current directory. But the oder
of the first output and second output should be the same. For synchronous operation, the
second `console.log` statement will be executed only after the directory is read and the
the first `console.log` is executed.

```
fs = require('fs');

function getFiles(err, files){
    console.log('files:', files);
}

fs.readdir('./', getFiles);

console.log('users are waiting');

------------------------------
output:
users are waiting
files: [ '.idea', 'HelloWorld.html', 'async-demo.js', 'sync-demo.js' ]
```

When we use asynchronous operation, the second `console.log` is executed before the 
`fs.readdir` function is finished. Here, we have a callback function `getFiles`. 
After `fs.readdir` finishes reading files, it would go to callback function and print
out the files' names. Therefore, we can interact with users with our system is busy
reading data from file system.

## Benefits and Features

The biggest benefit for using Node is we can use the same language between the back end
and the front end. It will make development more efficient since we only need to focus on
one language. Also, JavaScript is a dynamic language which means the type of a variable
is determined by its value, not when the variable is declared. Another important feature
and benefit for Node or JavaScript is the convenience of using JSON to pass data from back
end to front end. Since JSON is based on a subset of JavaScript, it can be naturally handled
by JavaScript.