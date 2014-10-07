
# Javascript Developer

## Language Problems

### Context Binding

Make the following code work (ie. should output only "Hello world" to the
console) without writing any **new** functions or changing any code outside of the
`bind` function. Explain what you did and why/when this would be useful.


```javascript

function bind(func, context) {
  // TODO implement this function
}

function sayHello() {
  console.log(this.bar);
}

var Foo = function() {
  this.bar = 'Hello World';
};

var foo = new Foo();
bind(sayHello, foo)();
```

## jQuery / DOM Problems
## Framework / Design Problems

