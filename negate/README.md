# `negate`

[home](../README.md) &gt; `negate`

Ramda's [`negate`](http://ramdajs.com/docs/#negate) does exactly what you'd expect it to do:

```js
import { negate } from 'ramda'

negate(5)    // returns -5
negate(-5)   // returns 5
negate('5')  // returns -5
negate([5])  // returns NaN
negate({})   // returns NaN
```

Interestingly, if we call `negate` without an argument, it returns itself. We can do this:

```js
const n1 = negate
const n2 = negate()

n1(5)  // returns -5
n2(5)  // returns -5
```

Uh, why? Not sure, but my guess is that this is a consequence of Ramda functions being curriable. But that's just a guess.

[Solutions](./solutions.md)
