# `merge`

[home](../README.md) &gt; [`merge`](./README.md) &gt; solutions

```js
const merge = (...args) => {
  const [x, ...xs] = args

  return x
    ? {
      ...x,
      ...merge(...xs)
    }
    : {}
}

// returns {"color": "yellow", "hex": "f00", "name": "Pearl"}
merge(
  { color: 'red', hex: 'f00' },
  { name: 'Pearl', color: 'yellow' }
)

// returns {"color": "red", "hex": "f00", "name": "Pearl"}
merge(
  { name: 'Pearl', color: 'yellow' },
  { color: 'red', hex: 'f00' }
)
```
