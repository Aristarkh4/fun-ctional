# `concat`

[home](../README.md) &gt; [`concat`](http://ramdajs.com/docs/#concat)

Returns the result of concatenating the given lists or strings. The Ramda `concat` bases the concatenation on the type of the first argument, so if the first argument is a String, then it will do string concatenation; if the first argument is an Array, then it will do array concatenation.

```js
concat([], [])                // returns []
concat([4, 5, 6], [1, 2, 3])  // returns [4, 5, 6, 1, 2, 3]
concat('ABC', 'DEF')          // returns 'ABCDEF'
```

[Solutions](./solutions.md)
