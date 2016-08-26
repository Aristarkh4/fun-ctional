# [range](./README.md)

```js
const range = (start, stop) => {
  return start < (stop - 1)
    ? [start, ...range(start + 1, stop)]
    : [start]
}

range(0, 10) // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
