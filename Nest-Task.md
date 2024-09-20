#node-nest 
#tasks

---

Написать 2 модуля:
- User
- Auth

В модуле `User`:
Контроллер:
- getAll
- getById
- updateById
Сервис:
- create
- getAll
- getOne
- update

В модуле `Auth`:
Контроллер:
- signUp
- signIn
Сервис:
- подключение `User` модуля
- signUp с созданием пользователя
- signIn
- все контроллеры возвращают `User`

Написать Guard для токена из заголовков
Все запросы валидируются при помощи `DTO` и `Pipes`

Контрольные вопросы:
- Что такое Pasport?
- Что можно достать из запроса?
- Как пользоваться `@Res` и `@Req`
- Как не отдавать некоторые поля модели пользуясь class-validator / class-transform?