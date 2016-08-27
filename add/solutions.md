# [add](./README.md)

First, let's make a curriable `add` function a la Ramda. There is probably a simpler way, but this works fine.

```js
import { isNil } from 'ramda'

const add = (a, b) => {
  if (isNil(a)) { return add }
  if (isNil(b)) { return (v) => add(a, v) }

  return a + b
}

const adder = add()
const addToFive = adder(5)

addToFive(10)           // returns 15
```

Next, let's try making an `add` function, not curriable, that will take any number of arguments and add them. (We can curry this up to a specific number of arguments with `curryN`.)

```js
const add = (x, ...xs) => x ? x + add(...xs) : 0

add()                   // returns 0
add(5)                  // returns 5
add(5, 10)              // returns 15
add(5, 10, 15)          // returns 30
add(5, 10, 15, 20)      // returns 50
```

And here is a version using `reduce`:

```js
import { reduce } from 'ramda'

const add = (...args) => reduce((a, v) => a + v, 0, args)

add(1, 2, 3, 4)         // returns 10
```

We can accomplish the same effect as Ramda's `add` with our `add`, and with any number of parameters, as long as we specify a number. To do this, we can use `curryN`:

```js
import { curryN } from 'ramda'

const add = (x, ...xs) => x ? x + add(...xs) : 0
const adder = curryN(4, add)

const add2 = adder(2)
const add6 = add2(4)
const add14 = add6(8)
add14(16)               // returns 30

adder(2)(4)(8, 16)      // returns 30
adder(2, 4)(8)(16)      // returns 30
adder(2, 4, 8)(16)      // returns 30
adder(2)(4)(8)(16)      // returns 30
```

So we could have made Ramda's `add` from ours like this:

```js
import { curryN } from 'ramda'

const add = (x, ...xs) => x ? x + add(...xs) : 0
const radd = curryN(2, add)

radd(5)(15)             // returns 20
radd(15, 5)             // returns 20
```
