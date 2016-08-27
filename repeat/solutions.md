# `repeat`

[home](../README.md) &gt; [`repeat`](./README.md) &gt; solutions

```js
const repeat = (s, n) => (n < 1) ? [] : [s, ...repeat(s, n - 1)]

repeat('x', 5)   // returns ['x', 'x', 'x', 'x', 'x']
repeat('y', 0)   // returns []
repeat('z', -5)  // returns []
```
