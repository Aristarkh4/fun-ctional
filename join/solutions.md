# [join](./README.md)

```js
import { reduce } from 'ramda'

const join = (sep, [x, ...xs]) => isEmpty(xs) ? x : x + sep + join(sep, xs)

join('', ['a', 'b', 'c', 'd', 'e', 'f', 'g'])  // returns 'abcdefg'
join('-', ['x', 'y', 'z'])                     // returns 'x-y-z'
```
