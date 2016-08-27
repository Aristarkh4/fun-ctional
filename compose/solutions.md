# `compose`

[home](../README.md) &gt; [`compose`](./README.md) &gt; solutions

Here's a solution using Ramda's `reduceRight`. We could also use `reverse` and `reduce` (see below), but `reduceRight` is simpler.

```js
import { head, inc, negate, reduceRight } from 'ramda'

const compose = (...funcs) => {
  return (...args) => head(
    reduceRight((acc, f) => [f(...acc)], args, funcs)
  )
}

const f = compose(inc, negate, Math.pow)

f(3, 4)            // returns -80

const g = compose(negate, inc, Math.pow)

g(3, 4)            // returns -82
```

Another option:

```js
import { head, inc, negate, reduce, reverse } from 'ramda'

const compose = (...funcs) => {
  return (...args) => head(
    reduce((acc, f) => [f(...acc)], args, reverse(funcs))
  )
}

const f = compose(inc, negate, Math.pow)

f(3, 4)            // returns -80

const g = compose(negate, inc, Math.pow)

g(3, 4)            // returns -82
```
