# `map`

[home](../README.md) &gt; [`map`](./README.md) &gt; solutions

```js
const map = (f, [x, ...xs]) => x ? [f(x), ...map(f, xs)] : []

const square = x => x * x

const a = [1, 2, 3, 4, 5]

map(square, a) // returns [1, 4, 9, 16, 25]
```
