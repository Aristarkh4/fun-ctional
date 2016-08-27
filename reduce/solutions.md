# `reduce`

[home](../README.md) &gt; [`reduce`](./README.md) &gt; solutions

```js
const reduce = (f, a, [x, ...xs]) => x ? reduce(f, f(a, x), xs) : a

const colors = [
  { name: 'red', hex: 'f00' },
  { name: 'green', hex: '0f0' },
  { name: 'blue', hex: '00f' },
  { name: 'magenta', hex: 'f0f' }
]

const upColor = (acc, clr) => [ ...acc, toUpper(clr.name) ]

reduce(upColor, [], colors) // returns ['RED', 'GREEN', 'BLUE', 'MAGENTA']
```
