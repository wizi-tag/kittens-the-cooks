```ts
interface User {
  readonly id: number;
  name: string;
  age?: number;
  friends?: User[];
  getName(): string;
}

const u: User = {
  id: 444,
  name: 'Bob',
  getName() {
    return this.name;
  },
}

console.log(u)
console.log(u.getName())
```