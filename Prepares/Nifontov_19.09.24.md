#typescript 
#prepare

Что такое TS?
Какие типы данных знаешь?
`any`, `unknown`, `never`, `void` - для чего, в чём разница?
- `any`
Как указывается тип?
- `unknown`
Что делать с `unknown`?
Что такое Type Guards?
Какие способы сужения типов ты знаешь?
- `never`
Как получить `never`?
Что такое `enum`, `tuple`?
Что такое Reverse Mapping?
Во что превращается enum после преобразования в JS?
Что такое `tuple`?
Что знаешь про алиасы и интерфейсы?
- `interfaces`
Как сделать какое-то свойство опциональным?
Как сделать какое-то свойство неизменяемым?
```ts
{
	name?: string 
}
//какой будет тип?
```
В чём разница типов и интерфейсов?
Можем ли мы имплементить типы к классам?
Чего я не могу сделать с интерфесами?
Что знаешь про `extends`?
Как расширить тип?
Разница `|` и `&`
Знаешь что-нибудь про литеральные типы?
Кастомные Type Guard
```ts
function isString(a): a is string {
	return(typeof a === 'string')
}

if (isString(a)) {
	// a: string
}
```
Как мне описать тип фунции?
```ts
type A = (a: number) => void;

const a: A = (num) => {
	console.log(a)
}
```
Как передавать неограниченное кол-во элементов?
Как указать что параметри необязательный?
Как указать значение по умолчанию?
Может ли поле быть и необязательным и со значением по умолчанию?
Что такое дженерики?
Как написать функцию дженерик которая вернёт длинну или число? 
Как сделать чтобы был только число или строка?
```ts
<T extends number | string>
```
Как пользоваться дженериками?
Как прокинуть дженерик в класс и интерфес?
Приведи практический пример испоьзования дженрика
> у тебя есть запрос  с типизацией Reqest. в Request может быть разное тело, через дженерик прокидываем конкретный payload 

Что знаешь про Utility types?
 ` Задачка на Pick & Omit `
Что знаешь про `Exclude` `Extract`?

Что знаешь про классы?
Что такое абстрактный класс?
Что такое абстрактное свойство?
Что такое абстрактный метод?
Какие модификаторы доступа ты знаешь?
Что такое `protected`?
Что значит `#`
// нельзя сочетать `#` и `private`

Для чего нужны абстрактные классы?
В чём их разница?
Приведи пример абстрактного класса
Что делает `static`?

Как имплементить типы и интерфейсы?

// mapped types 
// conditional types
