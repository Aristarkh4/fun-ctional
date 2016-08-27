# `partial`

[home](../README.md) &gt; [`partial`](./README.md) &gt; solutions

```js
import { add } from 'ramda'

const partial = (f, a) => (...b) => f(...a, ...b)

const addFour = (a, b, c, d) => a + b + c + d

const addTo1And2 = partial(addFour, [1, 2])
const addTo5 = partial(addFour, [5])

addTo1And2(3, 4)    // 10
addTo5(10, 15, 20)  // returns 50
```
