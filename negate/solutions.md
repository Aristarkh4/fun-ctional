# [negate](./README.md)

Because `NaN` is falsy, we can use a simple boolean expression to return `NaN` if the argument is not parsable as a number, and the negated, parsed number if it is. This doesn't provide the `negate()` returns a function feature, but we'll leave that for now.

```js
const negate = x => parseFloat(x) && -x

negate(5)        // returns -5
negate(-5)       // returns 5
negate('5')      // returns -5
negate([5])      // returns NaN
negate({})       // returns NaN
```

Sure enough, if we `curry` our negate function, then we get the behavior we observed in the Ramda version:

```js
const negate = curry(x => parseFloat(x) && -x)

const n1 = negate
const n2 = negate()

n1(5)            // returns -5
n2(5)            // returns -5
```
