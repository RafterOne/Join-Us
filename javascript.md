
# Javascript Developer

Extra points for creative solutions. Even if a "correct" solution cannot be
found an incorrect one can let us see what skills you have and start a
discussion.

## Language Problems

### Recursion

Count the number of strings in the `data` array and all nested arrays in
a recursive fashion.


```javascript
  var data = [
    "test",
    ["a", "b", "c"],
    [["x", "y"], "z"],
    "hello",
    "world",
    "something",
    ["a", ["b", "c"], "d", "b"]
  ];

  function countStrings(arr) {
    // implement only this function body
  }

  console.log("Strings: ", countStrings(data));
```


### Context Binding

Make the following code work (ie. should output only "Hello world" to the
console) by implementing the `bind` function or changing any code outside of the
`bind` function. Explain what you did and why/when this would be useful.


```javascript
// implement `bind` here

function sayHello() {
  console.log(this.bar);
}

var Foo = function() {
  this.bar = 'Hello World';
};

var foo = new Foo();
bind(sayHello, foo)();
```

### Instantiation Techniques

Make the following code work by implementing only the first method. Explain why
this method would be useful.

```javascript
function extend(obj) {
  // implement this function
}

var Foo = function(args) {
  extend(this, args);
}

var foo = new Foo({firstName: 'Hello', lastName: 'World'});

// should print Hello World
console.log(foo.firstName + ' ' + foo.lastName);
```

### Sorting

Sort the `data` array using the `position` property of each object from lowest
to highest. Assume each element of the array is an object with a position
property and it is a Number. Use Javascripts built-in `Array.sort`

```javascript 
var data = [
    {id:1, position: 10, name: 'foo'},
    {id:2, position: 12, name: 'bar'},
    {id:3, position: 1, name: 'foo'},
    {id:5, position: 20, name: 'foo'},
    {id:4, position: 4.5, name: 'bar'}
]

// sort here
```

## jQuery / DOM Problems


### Event Delegation

Log the HTML tag name of the element being clicked on. Explain 


```html
<p>
<strong>Hello</strong> <em>World</em> from javascript.
</p>
````

```javascript
jQuery('body').click(function(ev) {
    // print the tag name here
});
```

### Selectors

Toggle the display of the semantic children of header HTML tags (ie. make them
hidden/shown) whenever a parent *header* tag (h1, h2, h3, etc) is clicked. High
priority header tags should collapse all lower priority tags they contain (ie.
clicking `h1` collapses all `h2` tags in it's 'section'). Do not modify the
HTML.

Extra credit for brevity and/or creative solutions.

```html
<h1>Foo</h1>
<p>This is a test of the emergency broadcast system.</p>

<h2>Bar</h1>
<p>This is a test of the emergency broadcast system.</p>
<p>This is a test of the emergency broadcast system.</p>

<h3>Foo</h3>
<p>This is a test of the emergency broadcast system.</p>

<h3>Foo 2</h3>

<h1>Foo Bar</h1>

<h2>Bar Foo</h2>
<p>This is a test of the emergency broadcast system.</p>

<h1>Bar Bar</h1>
<p>This is a test of the emergency broadcast system.</p>

<h1>Foo Foo</h1>
<p>This is a test of the emergency broadcast system.</p>

<h2>Bar bar bar</h2>
<p>This is a test of the emergency broadcast system.</p>
<p>This is a test of the emergency broadcast system.</p>
```

```javascript
// implement the 'click' handler(s)
```

## Framework / Design Problems

### Dependency Injection

Write two functions: `register` and `using`. `register` takes a string and a
javascript object (function, object, string, ...). `using` takes an array of
strings and a function as it's arguments.

Your goal is for your `using` function to provide it's function argument with
all the items given in it's array argument previously registered via the
`register` function by that name. `using` should pass it's function arguments
containing these *dependencies* in the order specified in the array. See the
test code below for the intended usage.

The `using` function should fail if an string is provided that was not
previously registered.

Discuss why a system like this might be useful. Discuss current javascript
implementations of this pattern.

```javascript
// implement your register/using functions here
// you can have support variables/structures

register('Foo', "Hello World");
register('bar', function() { console.log("Hello World"); });
register('bam', { a: 'Hello', b: 'World'});

// the following should log "Hello World" to the console 3 times
using(['bam', 'bar', 'Foo'], function(a, b, c) {
    b();
    console.log(c);
    console.log(a.a, a.b);
});

// this should print "Invalid Service"
try {
    using(['box'], function() { console.log("Hello world"); });
} catch(e) {
    console.log(e);
}
```
