#typescript 
#exam 
#shapoval 

> *Никита Шаповал*
> *20.09.24*
---

Какие типы данных есть в TS?
Расскажи про `any`, `unknown`
Как начать работать с `unknown`?
Что такое сужение типов?
Как именно проверить тип помимо `typeof`?
Функция принимает объект, нужно проверить что этот объект это User?
Напиши функцию которая отправляет запрос
`url`
`method` // default - GET
`data` - any

Проверить внутри функции что data это объект User

```ts
interface IData {
	[key: any]: any;
}

user: unknown;

/*
// user
{
	id: 5,
	name: "Andrew"
}
*/

const data = request<User>('api/posts', 'GET');

async function request<T>(url: string, method='GET': HttpMethod, data?: IData): T {
	const response = await fetch(url);
	// check response type
	return response
}

```

Что слышал про `is`?
Расскажи про `never` и `void`?

Для чего использовать кортежи?

```ts
type MyTuple = [string, [number, number]];
// ['circle', 1, 2]

type TypeArray = string | number

let a: TypeArray[] = [1, 2, 3];
let b: <string | number>[] = [1, 2, 3]
let c: <ReadOnlyArray>[] = []
```

Как создать массив значений?
Как создать массив с числами или строками? Не создавая отдельный тип?
Как создать массив который нельзя будет изменять?

Расскажи про перечисления
Давай сделаем из задачи с функцтей request тип method - `enum`

```ts
enum HTTP_METHODS = {
	GET = 10,
	POST,
	PUT = 'PUT',
	DELETE,
}
```
Как получить union всех полей `enum`?

Чем отличается интерфейс от типа?
Где может пригодиться переобъявление интрефейса?
Как объявить функцию интрфейсом?

```ts
interface MyFunc {
	(url: string): void
}
```

Как сделать поле интерфейса опциональным?
Как сделать поле только для чтения?

Можно ли сделать так?
```ts
interface IData {
	[key: string]: User;
	count: number;
}
```
(да, но нужно поправить)

Что такое дженерики?
```ts
interface IResponseData<T> {
	error: srting;
	status: number;
	data: T
}
```

Как добавить значение дженерика по умолчанию?
Как ограничить тип дженерика?

Задачка:
```ts
function forEach(arr, cb) {
	return arr.forEach(cb);
}
```

Расскажи про наследования, union, intersection
Можно ли `extend` несколько `interface`
Можно ли `implement` несколько `interface`

Какие утилиты работатют с пересечениями?

```ts
Exclude<string | number[] | number | {id: string}, >
```
Как исключить строки и числа?

```ts
Exclude<string | number[] | number | {id: string}, {length: number}>
```
Исключит ли это `string` и `number[]`?
