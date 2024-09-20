```ts
function createMap<T>(list: T[]) {

  return function<U>(cb: (num: T) => U): U[] {
    const result:U[] = [];
    for (let el of list) {
      result.push(cb(el))
    }
    return result;
  }
}

const mapNums = createMap([1, 2, 3])
const result = mapNums((num) => num + 2)

console.log(result)
```