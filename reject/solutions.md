# [reject](./README.md)

```js
import { reduce } from 'ramda'

const reject = (f, a) => reduce((a, v) => f(v) ? a : [...a, v], [], a)

const isOdd = x => x % 2 === 1

const a = [1, 2, 3, 4, 5]

reject(isOdd, a) // returns [2, 4]
```
