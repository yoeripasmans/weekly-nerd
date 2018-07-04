# ES6 To the rescue

In this article, I will cover some of the most important features in ES6. It will be helpful if you are new to ES6 or learning front-end frameworks.

## Let

The keyword `let` allows us creating block scopes in JavaScript. Let’s see some examples.

### Block scope
Using var.
```js
var me = 'James Bond';

if(true) {
  var me = 'Chuck Norris';
}

console.log(me);
// Chuck Norris
```

Using let.
```js
let me = 'James Bond';

if(true) {
  let me = 'Chuck Norris';
}

console.log(me);
// James Bond
```

## Const

Constants are block-scoped, much like variables defined using the let statement. The value of a constant cannot change through re-assignment, and it can't be redeclared.

```js
const foo = 10;
foo = 5; // Shows error. You cannot change the value of const.
const bar = 'Constant variable';
bar = 'Assigning new value'; // Shows error.
```

## Arrow functions
The arrow functions at first might seem confusing, but after a while, you can understand their shorter syntax and the magic of the scope of this. See the example below.

### Example of arrow function
```js
let newWay = (name, nickname) => {
  return 'My name is ' + nickname + ', ' + name;
};

console.log( newWay('James Bond', 'Bond') );
// My name is Bond, James Bond
```

### Scope
Without arrow functions.

```js
var sandwich = {
  bread: 'white',
  cheese: 'blue',

  prepare: function() {
    return 'I want a sandwich with ' + this.bread + ' bread and ' + this.cheese + ' cheese';
  },

  make: function() {
    var that = this;
    window.setTimeout( function () {
      console.log( that.prepare() );
    }, 100 );
  }

};

// sandwich.make();
// I want a sandwich with white bread and blue cheese
```
With arrow functions.
```js
let newSandwich = {
  bread: 'white',
  cheese: 'blue',

  prepare: function() {
    return 'I want a sandwich with ' + this.bread + ' bread and ' + this.cheese + ' cheese';
  },

  make: function() {
    window.setTimeout( () => console.log(this.prepare()), 100 );
  }

};

// newSandwich.make();
// I want a sandwich with white bread and blue cheese
```
## Spread operator

The spread operator allow us extract/expand data from an array make our lifes easier. Confused? I guess I could not explain. Go to practice. Imagine the following arrays:

```js
let actors = ['James Bond', 'Chuck Norris', 'Jason Bourne'];
let newCharacters = ['Bruce', 'Kitana'];
```
If we had to add the new actors to the main array, we could try something like that:

```js
actors.push(newCharacters);

console.log(actors);
// ['James Bond', 'Chuck Norris', 'Jason Bourne', ['Bruce', 'Kitana']]
```
The data is there, but not in the way that we want. So we need to manipulate it before:
```js
newCharacters.forEach(function(actor) {
  actors.push(actor);
});

console.log(actors);
// ['James Bond', 'Chuck Norris', 'Jason Bourne', 'Bruce', 'Kitana']
```
The operator spread arrives making magic and leaving everything beautiful.
```js
actors.push(...newCharacters);

console.log(actors);
// ['James Bond', 'Chuck Norris', 'Jason Bourne', 'Bruce', 'Kitana']
```

## Sources

- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
- [https://es6.io/](https://es6.io/)
- [http://es6-features.org/#Constants](http://es6-features.org/#Constants)
