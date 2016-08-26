# [omit](./README.md)

```js
import { contains, reduce } from 'ramda'

const bob = { name: 'Bob', age: 75, eyes: 'blue' }
const ted = { name: 'Ted', age: 40, eyes: 'brown', weight: 82 }

const omit = (keys, obj) => {
  return reduce(
    (acc, key) => contains(key, keys) ? acc : { ...acc, [key]: obj[key] },
    {},
    Object.keys(obj)
  )
}

omit(['age', 'eyes'], bob) // {"name": "Bob"}
omit(['eyes', 'weight'], ted) // {"age": 40, "name": "Ted"}
omit(['iq'], bob) // {"age": 75, "eyes": "blue", "name": "Bob"}
omit(['name', 'age', 'eyes', 'weight'], ted) // {}
```
