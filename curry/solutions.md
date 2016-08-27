# `curry`

[home](../README.md) &gt; [`curry`](./README.md) &gt; solutions

The `curry` function works only when provided with a function with finite arity (number of parameters). So if we want to use it with a function that takes any number of arguments (i.e., ...args), then we'll need to specify how far down we want to curry it. That's where `curryN` comes in. The `n` parameter is the number of parameters to curry.

We can then curry a function `f` with a finite number of parameters by checking `f.length` and using `curryN` with `n` set to that length.

Our `curryN` function keeps accepting arguments and returning functions that take the remaining parameters until `n` is met or exceeded, in which case it applies the function with the collected arguments. We do this recursively.

```js
const curryN = (n, f) => {
  const curried = (...a) => (a.length >= n)
    ? f(...a)
    : (...b) => curried(...a, ...b)

  return curried
}

const curry = (f) => curryN(f.length, f)

const addFour = (a, b, c, d) => a + b + c + d

const f = curry(addFour)  // returns curried addFour
const g = f(1, 2)         // encloses 1, 2, returns addFour waiting for 2 more
const h = g(3)            // encloses 1, 2, 3, returns addFor expecting last number
h(4)                      // returns 10 (1 + 2 + 3 + 4)
```

Now, how can we implement `__` as a placeholder?

Well, the first thing to consider is that it is not used when we curry the function, but when we *call* the curried function. So it needs to be something that our curried function takes into account. And when it gets a placeholder instead of a value parameter, it has to know to return a function that takes that parameter and inserts it in the right position when it applies the curried function.

In other words, when we have a situation such as this:

```js
g(_, _, 3)
```

We need to return a function that takes two more arguments *and places them in the first two positions*. And when we call the function like this:

```js
g(1, 2, 3)
g(_, 2, 3)(1)
g(_, _, 3)(1)(2)
g(_, _, 3)(1, 2)
```

It needs to get those arguments into the right parameters.

One thing to notice above is that *each time the function is called* the arguments appear in the order of their position. Take this example:

```js
g(_, 2)(_, 3)(1)
```

The first call fills the second parameter and leaves the first and third undefined. The second call then needs to fill the first and third parameters. It leaves the first undefined again and fills the third. The third call fills that first parameter, the only one left undefined.

So suppose we started with an array of three undefined values:

```js
[undefined, undefined, undefined]
```

Then on each pass we took the arguments passed and filled in any *undefined values*. We'd get this:

```js
g(_, 2)  // [undefined, 2, undefined]
(_, 3)   // [undefined, 2, 3]
(1)      // [1, 2, 3]
```

Let's create a function to curry that will make it easy to see if we got it right:

```
const g = (x, y, z) => (x * 100) + (y * 10) + z

g(1, 2, 3)   // returns 123
```

What if we declared a constant `_` as `undefined`?

```js
const _ = undefined
```

Now we can pass that to our curried function. So let's write the function. We'll do a mutable version to start:

```js
const _ = undefined

const filled = (n, a) => reject(isNil, a).length === n

const curryN = (n, f) => {
  let params = repeat(undefined, n)

  const curried = (...args) => {
    params = map(v => v ? v : args.shift(), params)

    if (filled(n, params)) {
      const out = params
      params = repeat(undefined, n)
      return f(...out)
    }

    return curried
  }

  return curried
}

const curry = (f) => curryN(f.length, f)

const g = curry((x, y, z) => (x * 100) + (y * 10) + z)

g(1, 2, 3)          // returns 123
g(_, 2, 3)(1)       // returns 123
g(_, _, 3)(1)(2)    // returns 123
g(_, _, 3)(1, 2)    // returns 123
g(_, 2, _)(1, 3)    // returns 123
g(_, 2)(1)(3)       // returns 123
g(_, 2)(1, 3)       // returns 123
g(_, 2)(_, 3)(1)    // returns 123
```

Well, it's ugly and it's mutable, but it works. Not too bad for a first pass.
