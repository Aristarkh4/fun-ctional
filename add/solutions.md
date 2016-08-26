# [add](./README.md)

```js
import { reduce } from 'ramda'

const add = (...args) => reduce((a, v) => a + v, 0, args)

add(1, 2, 3, 4) // returns 10
```
