```ts
interface Xd<T> {
  value: T,
  values: T[],
  obj: {
    value: T
  }
}

class Xdd<T> implements Xd<T> {
  value: T;
  values: T[];
  obj: { value: T };
  constructor(input: T){
    this.value = input;
    this.values = [input, input, input]
    this.obj = {
      value: input
    }
  }
}

type CreateEntity  = {
  <T>(value: T): Xd<T>;
}

const createEntity:CreateEntity = <T>(value: T) => {
  return new Xdd(value);
}

console.log(createEntity(5));
```