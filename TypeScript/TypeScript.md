#typescript 
#tasks 
## Task_1

```ts
// Возможные роли пользователя - user/moderator/admin
// Tags: Enum, Union, Type, Interface

const user = {
  id: 1,
  login: 'test',
  role: 'user',
}

const checkPermissionsDecorator = (roles) => {
  return (user) => {
    return roles.includes(user.role);
  }
}
const checkPermission = checkPermissionsDecorator(['admin']);
const hasPermissions = checkPermission(user);
console.log(hasPermissions);
```
[Solution](TypeScript/Solutions/Task_1)

## Task_2

```js
// Виды пасты - spagetti/penne/macaroni
// Tags: Union, Enum, Narrowing
class Pizza {
  hasPepperoni;
  hasSauce;
  hasCheese;
  bakeTime = 30;
  constructor(hasPepperoni, hasSauce, hasCheese) {
    this.hasPepperoni = hasPepperoni;
    this.hasSauce = hasSauce;
    this.hasCheese = hasCheese;
  }
  bake() {
    setTimeout(console.log, this.bakeTime, 'Enjoy your pizza!');
  }
}
class Pasta {
  pastaType;
  hasSauce;
  hasCheese;
  cookTime = 30;
  constructor(pastaType, hasSauce, hasCheese) {
    this.pastaType = pastaType;
    this.hasCheese = hasCheese;
    this.hasSauce = hasSauce;
  }
  cook() {
    setTimeout(console.log, this.cookTime, 'Enjoy your pasta!');
  }
}
class Kitchen {
  makeDish(dish) {
    // эту часть надо переделать
    if ('bake' in dish) {
      dish.bake();
      return dish;
    } else if ('cook' in dish) {
      dish.cook();
      return dish;
    }
    throw new Error('Unknown dish');
  }
}
const kitchen = new Kitchen();
const pizza = new Pizza(true, true, false);
const pasta = new Pasta('spagetti', true, true);
kitchen.makeDish(pizza);
kitchen.makeDish(pasta);
```
[Solution](TypeScript/Solutions/Task_2)

## Task_3

```ts
// есть функция - которая возвращает кортеж
// в кортеже первый элемент всегда строка, 
// второй - аргумент функции (может быть абсолютно любого типа)

const fu = (a) => ['hi', a]
console.log(fu(1))
console.log(fu('1'))
console.log(fu(true))
// нужно ее типизировать
```
[Solution](TypeScript/Solutions/Task_3)

# Task_4

```ts
// типизировать массивы
const arr = [false, 5, 5, 5, true];
const arr2 = [false, 5, true];
const arr3 = [true, 1, 2, 3, 4, 5, true];

console.log(arr)
console.log(arr2)
console.log(arr3)
```
[Solution](TypeScript/Solutions/Task_4)

## Task_5

```tsx
// {
//  value: 5;
//  values: [5, 5, 5];
//  obj: {'value': 5};
//}

class Xdd {
  value;
  values;
  obj;
  constructor(){
  
  }
}

const createEntity = (value) => {
  return new Xdd(value);
}

console.log(createEntity(5));
```
[Solution](TypeScript/Solutions/Task_5)

## Task_6

```tsx
// Tags: Generic, Enum ('small' | 'large' | 'medium'), 
// Union, Interface, implements

class Shop {
  items = [];

  addGood(item) {
      return this.items.push(item);
  }

  get goods() {
      return this.items;
  }
}

class BaseProduct {
  name;

  price;

  discount;

  constructor(name, price, discount) {
      this.name = name;
      this.price = price;
      this.discount = discount;
  }
}

class Banana extends BaseProduct {
  size;

  constructor(price, discount, size) {
      super('banan', price, discount);
      this.size = size;
  }
}

class IceCream extends BaseProduct {
  withGlace;

  constructor(price, discount, withGlace) {
      super(‘iceCream’, price, discount);
      this.withGlace = withGlace;
  }
}

const shop = new Shop();

const iceCream = new IceCream(10, 0, true);
const banana = new Banana(5, 0.1, 'small');

shop.addGood(iceCream);
shop.addGood(banana);

console.log(shop.goods);
```
[Solution](TypeScript/Solutions/Task_6)

## Task_7

```ts
const user = {
    id: 1,
    name: 'Test',
    role: 'user',
};

user.age = 20;

const hasPermissions = (user: User) => {
    if (user.role === 'admin') return true;
    else if (user.role === 'moderator') return true;
    else if (user.role === 'user') return false;
    throw new Error('Unknown user role');
};

const createCounter = (initial = 0, error = 'Unauthorized') => {
    let count = initial;

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
    }
}
```
[Solution](TypeScript/Solutions/Task_7)

## Task_8

```tsx
// Опишите типы для двух функций:

export function keys(obj) {
  const currentKeys = [];
  
  for (let key in obj) {
    if (obj.hasOwnProperty(key)) {
	    currentKeys.push(key);
	}
  }
  
  return currentKeys;
}

export function values(obj) {
  const currentValues = [];
  
  for (let key in obj) {
    currentValues.push(obj[key]);
  }

  return currentValues;
}
```
[Solution](TypeScript/Solutions/Task_8)

## Task_9

```ts
function prop(key, obj) {
  return obj[key];
}

console.log(prop("a", {a:232, b: "gggg"}))
```
[Solution](TypeScript/Solutions/Task_9)

## Task_10

```ts
// Опишите типы для следующей функции:

export function createMap(list) {
  return function(cb) {
    const result = [];
    
    for (let el of list) {
      result.push(cb(el))
    }

    return result;
  }
}

const mapNums = createMap([1, 2, 3])
const result = mapNums((num) => num + 200)

console.log(result)
```
[Solution](TypeScript/Solutions/Task_10)

## Task_11

```ts
/*
Напиши интерфейс для объекта  user, 
в котором будет id, 
name - строка, 
age (опциональное),  
friends - массив юзеров 
и метод getName - который консолит имя пользователя
*/
```
[Solution](TypeScript/Solutions/Task_11)

## Task_12

```ts
/*
и еще задача: напиши функцию, которая может принимать на 
вход либо строку, либо массив строк. Если это строка, то вернуть 
надо строку с заглавными буквами, а если это массив, то верни 
массив со строками с заглавными буквами
типа:

'srt' => 'SRT'
['srt', 'trf'] => ['SRT', 'TRF']
*/
```
[Solution](TypeScript/Solutions/Task_12)

## Task_13

```ts
const flattenConstructor = () => {
  return (dict)=> Object.values(dict);
};

const flat1 = flattenConstructor();
const r1 = flat1({ a: 1, b: 2 });
console.log(r1);

const flat2 = flattenConstructor();
const r2 = flat2({ a: '1', b: '2' });
console.log(r2);
```
[Solution](TypeScript/Solutions/Task_13)

## Task_14

```ts
// Tags: Generic, Union

class Queue {
 tasks = [];

 delay = 10;

 runQueue() {
      setTimeout(() => this.doJob(), this.delay);
  }

 doJob() {
      const task = this.tasks.shift();
      if (task != null) {
          console.log(task);
      }
      this.runQueue();
  }

  addJob(task) {
      return this.tasks.push(task);
  }

  run() {
      this.runQueue();
  }

  set jobDelay(time) {
      this.delay = time;
  }
}

class Task {
  value;

  constructor(value) {
      this.value = value;
  }
}

const queue = new Queue();

const task1 = new Task('task#1');
const task2 = new Task(1);

queue.jobDelay = 1000;

queue.addJob(task1);
queue.addJob(task2);

queue.run();
```
[Solution](TypeScript/Solutions/Task_14)

## Task_15

```ts
// написать функцию которая принимает объект
// возвращает этот объект с доп полем keys которое содержит количество ключей
```
[Solution](TypeScript/Solutions/Task_15)

## Task_16

```ts
// протипизировать массив
// вложенность может быть любая

const array: MyArray = [1, [1, 2, [3, 4, [2, []]]]]
```
[Solution](TypeScript/Solutions/Task_16)

