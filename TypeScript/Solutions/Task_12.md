```ts
interface fn2<T> {
  (value: T): T
}

const qqq:fn2<string | string[]> = (value) => {
  if(typeof value === 'string'){
    return value.toUpperCase();
  }
  else if(Array.isArray(value)){
    return value.map(item => {return item.toUpperCase()})
  }
  return value;
}

console.log(qqq('fff'))
console.log(qqq(['gg', 'ff']))
```