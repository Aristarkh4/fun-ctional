# [zip](./README.md)

```js
import { isNil } from 'ramda'

const zip = (left, right) => {
  const [l, ...ls] = left
  const [r, ...rs] = right

  if (isNil(l) || isNil(r)) { return [] }

  return [[l, r], ...zip(ls, rs)]
}

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
