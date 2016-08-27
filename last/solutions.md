# `last`

[home](../README.md) &gt; [`last`](./README.md) &gt; solutions

```js
import { isEmpty } from 'ramda'

const last = ([x, ...xs]) => isEmpty(xs) ? x : last(xs)

const a = [1, 2, 3, 4, 5]

last([])  // returns undefined
last(a)   // returns 5
```
