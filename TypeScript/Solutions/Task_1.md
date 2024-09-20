```ts
// Возможные роли пользователя - user/moderator/admin
// Tags: Enum, Union, Type, Interface

enum Roles {
  user = "user",
  moderator = "moderator",
  admin = "admin"
}

interface User {
  id: number;
  login: string;
  role: Roles;
}

const user: User = {
  id: 1,
  login: 'test',
  role: Roles.user,
}

type CheckPermissionsFunction = {
  (user: User): boolean
}

type CheckPermissionsDecorator = {
  (roles: Roles[]): CheckPermissionsFunction
}

const checkPermissionsDecorator: CheckPermissionsDecorator = (roles) => {
  return (user: User) => {
    return roles.includes(user.role);
  }
}
const checkPermission = checkPermissionsDecorator([Roles.admin]);
const hasPermissions = checkPermission(user);
console.log(hasPermissions);
```
