```ts
export function keys<O extends object>(obj: O): Array<keyof O> {
  const currentKeys: Array<keyof O> = [];

  for (let key in obj) {
    if (obj.hasOwnProperty(key)) {
	    currentKeys.push(key);
	}
  }

  return currentKeys;
}

console.log(keys({
  age: 33,
  name: "georg"
}))
 
export function values<O extends object>(obj: O): Array<O[keyof O]> {
  const currentValues: Array<O[keyof O]> = [];

  for (let key in obj) {
    currentValues.push(obj[key]);
  }

  return currentValues;
}

console.log(values({
  age: 33,
  name: "georg"
}))
```