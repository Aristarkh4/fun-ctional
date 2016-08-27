# `remove`

[home](../README.md) &gt; [`remove`](./README.md) &gt; solutions

```js
import { head, reduce } from 'ramda'

const remove = (x, y, c) => {
  return head(reduce(
    ([a, i], v) =>  (i >= x && i < (x + y)) ? [a, ++i] : [[...a, v], ++i],
    [[], 0],
    c
  ))
}

const a = [1, 2, 3, 4, 5]

remove(5, 10, a)    // returns [1, 2, 3, 4, 5]
remove(4, 2, a)     // returns [1, 2, 3, 4]
remove(-7, 10, a)   // returns [4, 5]
remove(2, 4, a)     // returns [1, 2]
```
