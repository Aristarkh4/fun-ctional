# `reverse`

[home](../README.md) &gt; [`reverse`](./README.md) &gt; solutions

```js
const reverse = ([x, ...xs]) => x ? [...reverse(xs), x] : []

reverse([1, 2, 3, 4, 5, 6, 7]) // returns [7, 6, 5, 4, 3, 2, 1]
```
