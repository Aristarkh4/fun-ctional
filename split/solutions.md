# `split`

[home](../README.md) &gt; [`split`](./README.md) &gt; solutions

```js
import { drop, indexOf, take } from 'ramda'

const split = (sep, str) => {
  const i = indexOf(sep, str)
  const w = sep.length

  return i < 0
    ? [str]
    : [take(i, str), ...split(sep, drop(i + w, str))]
}

split('cd', 'abcdefg')  // returns [ab', 'efg']
split('x', 'xyzxyzxyz') // returns ['', 'yz', 'yz', 'yz']
```
