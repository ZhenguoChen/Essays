# JavaScript: this

**Zhenguo Chen**

## Introduction

The `this` keyword exists in most modern programming languages. In most the these languages, `this` has similar
usage. For instance, in C++, `this` is a constant pointer that holds the memory address of the current object
which means `this` is always connected with current object. However, in JavaScript, `this` has a different usage. 
The value of `this` is determined by how a function is called, this means it may be different each time the
function is called. Here, we will go through four of the most common situations.

## Usage

### 1. Global Context

In global execution context, `this` is the global object (in browser, it is the `window` object), regardless of the fact you are in strict mode or not. Therefore, `console.log(this == window)` will print out true in console. Also, 
when you declare `this.b = 'b'`, you will get `window.b = 'b'`.

```js
console.log(this == window); //true
this.b = 'b';
console.log(window.b); // 'b'
```

### 2. Function Context

When it comes to function, the value of `this` depends on how the function is called. 

#### 2.1 non-strict mode

When you use `this` inside a function defined in global context, `this` is still bound to global object.

```js
function f(){
    return this;
}
console.log(f()); // window
```

#### 2.2 strict mode

However, it behaves differently under `strict mode`. The value of `this` remains at whatever it was set to as compared to when entered during the execution context. In the following code, in `strict mode`, `this` is not defined by the execution
context. So, it remains `undefined`.

```js
function f2() {
    'use strict'; // strict mode
    return this;
}

console.log(f2() == undefined); // True
```

#### 2.3 inner function

This is where `this` confuses most people, because you may think, in function invocation, `this` is the same in an
inner function as in the outer function. However, the truth is, the context of inner function depends only on 
invocation, and not on the outer function's context. Let's take a look at the following code:

```js
var obj = {
    name: "object",
    method: function () {
        function f() {
            return this + ":" +this.name;
        };
        return f(); 
    }
};

console.log(obj.method()); // undefined
```

Since function `f` is defined inside `obj`, you may expect to have `this` as our `obj`. However, `f` is 
actually an inner function which has a different context compared with its outer function. To get expected result,
`f` should be executed with the same context as the `method` function. We can modify the inner function's context
with indirect invocation by using `.call` or `.apply()`.

```js
var obj = {
    name: "object",
    method: function () {
        function f() {
            return this + ":" +this.name;
        };
        return f.call(this);
    }
};

console.log(obj.method()); //object
```

### 3. Method Context

A method is a function stored as a property of an object. When you want to invoke a method, you need to use `obj.f()`.
A method invocation is different from a function invocation. It is important for you to distinguish a method 
invocation from a function invocation.

```js
var obj = {
    f: function () {
        return 1; 
    }
};

obj.f(); // method invocation
var f2 = obj.f;
f2(); // method invocation
```

#### 3.1 method invocation

When we invoke a method, `this` is the object itself. In the following example, function `f` is a method of `obj`,
so `this` is the object itself. Therefore, `this.name` refers to `obj.name`.

```js
var obj = {
    name: "object",
    f: function () {
        return this.name;
    }
};

console.log(obj.f()); // hi
```

#### 3.2 function invocation

As mentioned above, method can be extracted from object and converted to a function by using 'var f2 = obj.f'. In 
this case, the method is detached from the original object, and `f2()` is a function invocation rather than a method
invocation, which means `this` is in the global context. Therefore, the output for the following example is `undefined`.

```js
var obj = {
    name: "object",
    f: function () {
        return this.name;
    }
};

var f2 = obj.f;
console.log(f2()); // undefined
```

We can use `.bind` to fix the context, binding function with object. Once we bind a function with an object, it
will work as a method invocation. Therefore, the following example will get output `object`.

```js
var obj = {
    name: "object",
    f: function () {
        return this.name;
    }
};

var f2 = obj.f;

console.log(f2.bind(obj)());
```

### 4. Constructor Context

In JavaScript, there is also a `new` keyword which creates a new object. When `new` is followed by an expression 
that evaluates to a function object, constructor invocation is performed. Let's take a look at the following example:

```js
function People(name, sex) {
    this.name = name;
    this.sex = sex;
}

var me = new People('Zach', 'male');
console.log(me.name); // Zach
```

Here, the `new People('Zach', 'male')` is a constructor invocation of the People function and `me` is assigned a new
object. You can also define constructor in `class`.

```js
class People {
    constructor(name, sex){
        this.name = name;
        this.sex = sex;
    }
}

var me = new People('Zach', 'male');
console.log(me.name); // Zach
```

Here `var me = new People('Zach', 'male');` is also a constructor invocation, and the object initialization is 
handled by constructor method. `this` here refers to this newly created object.

## Conclusion

These are just four of the most common situations where `this` is used. There are also some other situations in
which `this` have different usages, such as arrow function and bound function. The examples above are tested under
Node.js 8. If you get any different results (it is possible, JavaScript is so weird), feel free to leave a 
comment below!

## Reference:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this
http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/
