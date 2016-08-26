# [zip](./README.md)

```js
const zip = ([l, ...ls], [r, ...rs]) =>
  (l === undefined || r === undefined)
    ? []
    : [[l, r], ...zip(ls, rs)]

const a = [1, 2, 3, 4, 5]
const b = [6, 7, 8, 9]

zip(a, b)  // returns [[1, 6], [2, 7], [3, 8], [4, 9]]
zip([], b) // returns []
zip(a, []) // returns []
```

```js
import { head, reduce } from 'ramda'

const zip = (left, right) => {
  return head(reduce(
    ([acc, [x, ...xs]], v) => (!x || !v) ? [acc, []] : [[...acc, [x, v]], xs],
    [[], left],
    right
  ))
}

const a = [1, 2, 3, 4, 5]
const b = [6, 7, 8, 9]

zip(a, b)  // returns [[1, 6], [2, 7], [3, 8], [4, 9]]
zip([], b) // returns []
zip(a, []) // returns []
```
