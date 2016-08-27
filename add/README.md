# add

Ramda's [`add`](http://ramdajs.com/docs/#add) adds two values together and returns the sum.

Why only two values? Why not however many are supplied as arguments? Because Ramda's `add` function is *curried*. That is, you can call it with a single argument and get back a function that takes a single argument and adds it to the first.

We'll write a curried `add` function and a second uncurried function that takes any number of arguments. Why do you suppose the second function must be uncurried? Try currying it and you'll see.

Ramda's `add` in action:

```js
import { add } from 'ramda'

add(2, 4)                       // returns 6

// returns a function that takes a number and adds 3 to it
const addToThree = add(3)

addToThree(7)                   // returns 10
```

Our own `add` function should allow any number of arguments:

```js
addEmUp(1, 2, 3, 4, 5)          // returns 15
addEmUp(5, 10, 15, 20)          // returns 50
```

We could make a subtract function, or we could just use Ramda's `negate` function for any value we wanted to subtract:

```js
addEmUp(5, 10, 15, negate(20))  // returns 10
```

[Solutions](./solutions.md)
