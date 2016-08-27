# `pick`

[home](../README.md) &gt; [`pick`](./README.md) &gt; solutions

```js
const bob = { name: 'Bob', age: 75, eyes: 'blue' }
const ted = { name: 'Ted', age: 40, eyes: 'brown', weight: 82 }

const pick = (keys, obj) => {
  return reduce(
    (acc, key) => contains(key, keys) ? { ...acc, [key]: obj[key] } : acc ,
    {},
    Object.keys(obj)
  )
}

pick(['iq'], bob) // {}
pick(['eyes', 'weight'], ted) // {"eyes": "brown", "weight": 82}
pick(['age', 'eyes'], bob) // {"age": 75, "eyes": "blue"}
pick(['name', 'age', 'eyes', 'weight'], ted) // {"age": 40, "eyes": "brown", "name": "Ted", "weight": 82}
```
