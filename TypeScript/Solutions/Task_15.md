```ts
interface Xd {
  keys: number;
}

function fn<O extends object>(obj: O): O&Xd {
  const obj2: O&Xd = Object.assign(obj, {keys: Object.keys(obj).length})
  return obj2;
}

console.log(fn({a: 4334, b: 'grer', c: 64}))
```