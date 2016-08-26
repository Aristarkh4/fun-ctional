# [pluck](./README.md)

```js
import { contains, reduce } from 'ramda'

const bob = { name: 'Bob', age: 75, eyes: 'blue' }
const ted = { name: 'Ted', age: 40, eyes: 'brown', weight: 82 }

const pluck = (keys, obj) => {
  return reduce(
    (acc, key) => contains(key, keys) ? { ...acc, [key]: obj[key] } : acc,
    {},
    Object.keys(obj)
  )
}

pluck(['eyes', 'weight'], ted)   // returns {"eyes": "brown", "weight": 82}
pluck(['iq'], bob)               // returns {}
pluck(['age', 'eyes'], bob)      // returns {"age": 75, "eyes": "blue"}

// returns {"age": 40, "eyes": "brown", "name": "Ted", "weight": 82}
pluck(['name', 'age', 'eyes', 'weight'], ted)
```
