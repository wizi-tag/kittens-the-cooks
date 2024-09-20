```ts
enum Roles {
  admin = 'admin',
  moderator = 'moderator',
  user = 'user'
};

interface User {
  id: number,
  name: string,
  role: Roles
  age?: number
};

const user: User = {
  id: 1,
  name: 'Test',
  role: Roles.moderator,
};

console.log(user);
user.age = 20;
console.log(user);

const hasPermissions = (user: User): boolean | never => {
  if (user.role === Roles.admin) return true;
  else if (user.role === Roles.moderator) return true;
  else if (user.role === Roles.user) return false;
  throw new Error('Unknown user role');
};

interface Counter {
  increment(): number | string;
  reset(): void;
};

interface CreateCounter {
  (initial?: number, error?: string): Counter;
};

const createCounter: CreateCounter = (initial: number = 0, error: string = 'Unauthorized') => {
  let count: number = initial;

  return {
    increment() {
      if (hasPermissions(user)) {
        count += 1;
        return count;
      }
      return error;
    },
    reset() {
      count = initial;
    }
  };
};

console.log(createCounter().increment());
```