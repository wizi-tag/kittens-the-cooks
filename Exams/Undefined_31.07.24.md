#typescript 
#exam 
#molodchenko

> *Сергей Молодченко* 
> *31.07.24*
---

какие типы данных есть в TS?
Отличие `void` & `never`?
Зачем нужен `unknown`?
Что делать с `unknown`?
Какие есть варинты сужения типа?
`in`, `typeof` это TS или JS?
Что такое guard type?
Как создать тип для объекта?
Что такое `interface` & `type`?
Как сделать...

```ts
interface IUser {
	id: string,
	name: string,
	age: number,
	greet(): string,
}

const user1: IUser {
	id: 'qwe-123',
	name: 'Albert',
	age: 20,
	greet: function(){ return `Hello my name is ${name}`},
}

const user2: IUser {
	id: 'asd-456',
	name: 'Beatrice',
	age: 35,
	greet: function(){ return `Hello my name is ${name}`},
}

const usersMap = {
	"qwe-123": user1,
	"asd-456": user2,
}
```

Как сделать интерфейс для объекта?
Как сделать интерфейс для функции?
Что такое дженерики?
Что такое декораторы?
Как браузер работает с TS?
Как типы и интерфейсы переводятся в TS?
Во что превращаются декораторы?
Что такое композиция декораторов?
Почему декораторы выполняются снизу вверх?