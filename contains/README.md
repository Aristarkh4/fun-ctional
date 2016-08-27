# `contains`

[home](../README.md) &gt; [`contains`](http://ramdajs.com/docs/#contains)

Returns true if the specified value is equal to at least one element of the given list; false otherwise. Ramda has its own `equals` function that it uses for comparison. We can import and use that, too.

```js
contains(3, [1, 2, 3])  // returns true
contains(4, [1, 2, 3])  // returns false
contains([42], [[42]])  // returns true
```

[Solutions](./solutions.md)
