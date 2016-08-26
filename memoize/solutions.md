# [memoize](./README.md)

```js
import { has } from 'ramda'

const memoize = f => {
  let memo = {}

  return n => {
    if (has(n, memo)) { return memo[n] }

    memo[n] = f(n)

    return memo[n]
  }
}

let count = 0

const factorial = memoize(n => {
  count += 1

  return product(range(1, n + 1))
})

factorial(5) // returns 120
factorial(5) // returns 120
factorial(5) // returns 120
count        // returns 1

factorial(7) // returns 5040
factorial(5) // returns 120
factorial(7) // returns 5040
count        // returns 2
```
