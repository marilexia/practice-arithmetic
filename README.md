JavaScript Arithmetic Lab
---

## Objectives

1. Practice doing math with JavaScript
2. Practice writing functions that do things with numbers
3. Practice parsing strings as numbers

## Introduction

In this lab, we're going to practice writing functions and manipulating numbers in JavaScript. First, though, we need to go over some basic math. In this lab, we're going to learn about various arithmetic operators. What's an operator, you say? It's a symbol that _operates_ on one or more (usually two) objects — `+` is a good example. The `+` operator says "add what's to the left of `+` and what's to the right of `+` together." Easy-peasy!

As you read through this lesson, you're going to be adding your solutions to `index.js`. You'll write a total of eight functions; use the results of running `learn test` in your IDE to guide you towards the right function names and functionality.

## Basic Math

The most fundamental math operations work as one might expect in JavaScript: `+` adds two numbers; `-` subtracts one number from another; `*` multiplies two numbers; and `/` divides one number by another. For example (as usual, follow along in console!)

``` javascript
1 + 80 // 81
60 - 40 // 20
2 * 3.4 // 6.8 (there's that floating-point arithmetic again...)
5.0 / 2.5 // 2
```

At this point, we can fix the first _four_ broken tests: we can define functions `add()`, `subtract()`, `multiply()`, `divide()` in `index.js`.

## Math + Assignment

Additionally, we can increment (`++`) and decrement (`--`) a number if it's assigned to a variable:

``` javascript
var number = 5

number++ // 5... hmmmm

number // 6 -- the number was incremented after it was evaluated

number-- // 6

number // 5
```

We can also put the incrementor and decrementor operations before the number:

``` javascript
--number // 4

++number // 5
```

But generally, you will see them placed _after_ the number (and we recommend that that's where you put them). If you're interested in the difference, take a look [here](http://jsforallof.us/2014/07/10/pre-increment-vs-post-increment/)

And, while we're on the subject, you'll usually only want to use these incrementors and decrementors when the shorthand makes what you're writing easier to read (more on when _exactly_ later). Instead, it's best to use the basic arithmetic operators combined with `=`. For the examples below, assume that `number` is equal to `5` (and resets for every example).

- `+=` modifies the value to the operator's left by adding to it the value to the operator's right:

```javascript
number += 3 // 8
```

- `-=` modifies the value to the operator's left by subtracting from it the value to the operator's right:

``` javascript
number -= 2 // 3
```

- `*=` modifies the value to the operator's left by multiplying it by the value to the operator's right:

``` javascript
number *= 10 // 50
```

- `/=` modifies the value to the operator's left by dividing it by the value to the operator's right:

``` javascript
number /= 5 // 1
```

The thing to remember about these methods is that they modify the variable in place. So if we have two functions that depend on the same external variable, the order in which they're called matters. Follow along in console:

``` javascript
var number = 10

function add5() {
  number += 5
}

function divideBy3() {
  number /= 3
}

divideBy3()

console.log(number) // 3.333333333335

add5()

console.log(number) // 8.333333333335

// reset number
number = 10

add5()

console.log(number) // 15

divideBy3()

console.log(number) // 5
```

**Because these methods are more explicit, prefer `+=` to `++` and `-=` to `--` (usually).**

Okay, now we're ready to write solutions for the next two functions: `inc(n)` and `dec(n)`.

## Parsing Numbers

Sometimes, we'll receive a number — well, we know it's a number, as we've seen many numbers in the past. JavaScript, however, won't know that it's a number because it shows up wrapped in quotes — JavaScript, then, thinks it's a string.

Luckily, JavaScript gives us tools to turn these strings into proper numbers (that is, numbers that JavaScript understands).

### `Number()`

The first such tool is the function `Number()`, which accepts one argument: the value to parse. 
So a typical call to `Number()` looks like

``` javascript
Number('2') // 2
```

What happens, though, if we pass utter nonsense to `Number()`? Go ahead and try it in the console — something like

``` javascript
Number('nonsense!')
```

What did it return? `NaN`? What is that?

`NaN` stands for "not a number" — pretty handy, right? This is the number (in the JavaScript sense) that JavaScript returns when it can't determine a valid value for a numeric operation.

