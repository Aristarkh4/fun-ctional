# [without](./README.md)

```js
const without = (w, a) => reduce((a, v) => contains(v, w) ? a : [...a, v], [], a)

without([2, 4], [1, 2, 3, 4, 5]) // returns [1, 3, 5]
without([1, 5], [1, 2, 3, 4, 5]) // returns [2, 3, 4]
```
