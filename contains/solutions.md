# `contains`

[home](../README.md) &gt; [`contains`](./README.md) &gt; solutions

First, let's do it with recursion and without `reduce`:

```js
import { equals } from 'ramda'

const contains = (n, [x, ...xs]) => equals(n, x) || contains(n, xs)

contains(3, [1, 2, 3])  // returns true
contains(4, [1, 2, 3])  // returns false
contains([42], [[42]])  // returns true
```


Here is one using `reduce`. Gotta love `reduce`.

```js
import { equals, reduce } from 'ramda'

const contains = (n, c) => reduce((a, v) => a || equals(n, v), false, c)

contains(3, [1, 2, 3])  // returns true
contains(4, [1, 2, 3])  // returns false
contains([42], [[42]])  // returns true
```
