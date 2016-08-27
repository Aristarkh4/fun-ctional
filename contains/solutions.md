# `contains`

[home](../README.md) &gt; [`contains`](./README.md) &gt; solutions

```js
import { reduce } from 'ramda'

const contains = (n, c) => reduce((a, v) => a || n === v, false, c)

const a = [1, 2, 3, 4, 5]

contains(3, a) // true
contains(7, a) // false
```
