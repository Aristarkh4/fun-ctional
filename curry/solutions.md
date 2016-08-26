# [curry](./README.md)

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
