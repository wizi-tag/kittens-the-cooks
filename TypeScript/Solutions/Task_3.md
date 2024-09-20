```ts
type Tuple<T> = [string, T]

const fu = <T>(a: T): Tuple<T> => ['hi', a]

console.log(fu(1))
console.log(fu('1'))
console.log(fu(true))
```