# [compose](./README.md)

```js
import { head, inc, negate, reduceRight } from 'ramda'

const compose = (...funcs) => {
  return (...args) => head(
    reduceRight((acc, f) => [f(...acc)], args, funcs)
  )
}

const f = compose(inc, negate, Math.pow)

f(3, 4)  // returns -80
```
