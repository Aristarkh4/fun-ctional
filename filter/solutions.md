# `filter`

[home](../README.md) &gt; [`filter`](./README.md) &gt; solutions

```js
import { reduce } from 'ramda'

const filter = (f, a) => reduce((a, v) => f(v) ? [...a, v] : a, [], a)

const isOdd = x => x % 2 === 1

const a = [1, 2, 3, 4, 5]

filter(isOdd, a) // returns [1, 3, 5]
```
