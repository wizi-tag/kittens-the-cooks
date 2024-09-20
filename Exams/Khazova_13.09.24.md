#typescript 
#exam
#pavlov

> *Дмитрий Павлов*
> *13.09.24*
---

Был ли опыт работы с TS
Как ты учила TS
Знаешь Utility Types?
Какие типы данных есть в TS?

```ts
const fn = (arg: unknown) => {
	return JSON.stringify(arg);
}
```

```ts
const fn = (arg: unknown): unknown => {
	return arg;
}
```

```ts
let a: any;

const fn = (arg: unknown): unknown => {
	return arg;
}

fn(a)
```

Как ты понимаешь `never`?

//Пустой массив - `never` ??????????

```ts
const fn = (): void => {
	console.log(1);
}

const fn = (): undefined => {
	console.log(1);
}
```

Расскажи о Union  
Какие утилиты для работы с Union знаешь? `Exclude`

Разница типов и интерфейсов

Наследовать интерфейс от интерфейса
Знаешь ключевое слово Implements?
Можем использовать класс как тип?

`//Начал писать абстрактные классы`

Расскажи о ключевом слове `as`
Стоит ли его использовать?

Как пользоваться сужением типов?

Что такое Generics?

Что такое перечисления?
```ts
enum MyEnum = {
	A = 123,
	B,
	C = "123",
	D,
	E = 5,
	F,
	G = 10,
	H = "4",
}
```

Разница `enum` и `const enum`
Знаешь ключевое слово satisfies?

Что такое модификаторы доступа?
`private` `protected` `public`

Можем ли мы использовать тернарники в типизации?

```ts
const A: <T extends object ? T : never>
```

