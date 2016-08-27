# `find`

[home](../README.md) &gt; [`find`](./README.md) &gt; solutions

```js
import { head, isEmpty, reduce } from 'ramda'

const find = (f, c) => head(
  reduce((a, v) => isEmpty(a) && f(v) ? [v] : a, [], c)
)

const isOdd = x => x % 2 === 1
const isEven = x => x % 2 === 0
const isThree = x => x === 3
const isEight = x => x === 8

const a = [1, 2, 3, 4, 5]

find(isOdd, a)   // returns 1
find(isEven, a)  // returns 2
find(isThree, a) // returns 3
find(isEight, a) // returns undefined
```
