# [slice](./README.md)

```js
import { head, reduce } from 'ramda'

const slice = (x, y, c) => {
  return head(reduce(
    ([a, i], v) =>  (i >= x && i < y) ? [[...a, v], ++i] : [a, ++i],
    [[], 0],
    c
  ))
}

const a = [1, 2, 3, 4, 5]

slice(-7, 10, a)   // returns [1, 2, 3, 4, 5]
slice(2, 4, a)     // returns [3, 4]
slice(4, 2, a)     // returns []
slice(5, 10, a)    // returns []
```
