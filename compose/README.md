# `compose`

[home](../README.md) &gt; [`compose`](http://ramdajs.com/docs/#compose)

Performs right-to-left function composition. The rightmost function may have any number of parameters (any "arity"); the remaining functions must take only one parameter (because it will be the output of the function to the right). In other words, they must be unary.

To use Ramda's example:

```js
import { compose, inc, negate } from 'ramda'

const f = compose(inc, negate, Math.pow);

f(3, 4);                // returns -80
```

How does this work? First the 3 and 4 are supplied to `Math.pow`, which returns 3 to the 4th power (3 * 3 * 3 * 3 = 81). That 81 is then supplied to `negate` which makes it -81. And that -81 is incremented by `inc`, which makes it -80. And that's what `f` returns.

If we swapped the order of `inc` and `negate` we'd get a different output:

```js
import { compose, inc, negate } from 'ramda'

const f = compose(negate, inc, Math.pow);

f(3, 4);                // returns -82
```

Now we get the same 81 from `Math.pow`, but first we increment it to 82, *then* we negate it to -82.

[Solutions](./solutions.md)
