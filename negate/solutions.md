# [negate](./README.md)

Because `NaN` is falsy, we can use a simple boolean expression to return `NaN` if the argument is not parsable as a number, and the negated, parsed number if it is. This doesn't provide the `negate()` returns a function feature, but we'll leave that for now.

```js
const negate = x => parseFloat(x) && -x
```
