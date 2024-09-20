```ts
type x = [boolean, ...number[], boolean];

const arr: x = [false, 5, 5, 5, true];
const arr2: x = [false, 5, true];
const arr3: x = [true, 1, 2, 3, 4, 5, true];

console.log(arr)
console.log(arr2)
console.log(arr3)
```