```ts
interface fn<O> {
  (dict: O): Array<O[keyof O]>
}

const flattenConstructor = <O extends object>(): fn<O> => {
  return (dict: O)=> Object.values(dict);
};

const flat1 = flattenConstructor();
const r1 = flat1({ a: 1, b: 2 });
console.log(r1);

const flat2 = flattenConstructor();
const r2 = flat2({ a: '1', b: '2' });
console.log(r2);
```