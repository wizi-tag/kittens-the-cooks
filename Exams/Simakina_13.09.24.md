#node-nest
#exam 
#molodchenko

> *Сергей Молодченко*
> *13.09.24*
---

Что такое нода?
Как происходит взаимодействие с другими файлами в NodeJS?
Что такое области видимости?
Сколько потоков нода использует для обработки запросов?
К чему приводит то что нода обрабатывает всё в одном потоке?
Что такое блокировка потока?
У нас может произойти блокировка потока при отправке запросов?
В каких случаях это может произойти?
Что такое Buffer?
Что такое Stream?
Что такое chunk? В виде чего он представлен?
Какие бывают стримы?
Какие есть способы чтения файла?
При работе через readFile может получиться ад колбэков. Как этого избежать? `fs/promises`
Как изменить середину файла?
Что такое `path`?
Что такое `os`?
Для чего может пригодиться?
Что такое `process`?
Что такое `http`?

---
Задача:
```
/uploads/
/uploads/jpeg
/uploads/png
/uploads/svg

/uploads/jpeg/some-image.jpeg

GET /file/some-image.jpeg
```
Напиши простой файловый сервер
Файлы лежат в папке uploads и отсортированны по папкам по расширению
с расширением `png` в папке `png`
с расширением `jpg` в папке `jpg`
с расширением `svg` в папке `svg`

Запрос:
`GET /file/some-image.png`
Ответ: 
`/uploads/png/some-image.png`

```ts
const http = require('http')

const server = http.createServer((req, res) => {
    if(req.method === "GET" && req.url.startsWith('/file')) {
        const [ image ] = req.url.split('/')[0].toReversed();
        const [imageName, ext] = image.split('.');
        if (ext === 'png') {
            fs.readFile(`uploads/${ext}/${image}`, (err, data) => {
                if(err) {
                    return console.log(err)
                }
                res.end(data)
            })
        }
    }
    
})
```
---
Что такое `Nest`?
Расскажи подробнее про архитектуру?
В чём отличие `Provider` от `Service`?
Как в контроллере получить тело запроса?
Что такое `Pipe`?
Что такое `DTO`?
Что такое `ORM`?
Что такое миграции?
Как задать отношение многие ко многим?

Переписать задачу на `Nest`
У файлов появляется `quality`
```
/uploads/
/uploads/png/some-image-q720.png
/uploads/png/some-image-q1080.png
/uploads/png/some-image-q1920.png

GET /file/some-image.jpeg?q=1080
```
Запрос:
`GET /file/some-image.png?quality=1080`

```ts
@Controller('file')
export class ImageController {
    constructor(private readonly imageService: ImageService) {}
    
    @Get()
    getImage(@Query() query: string, @Param() data: string){
      if(query){
        this.imageService.getImage(query, data);

    }
}

@Injecteble()
export class ImageServise {
    constructor(
        @InjectModel(Image)
        private readonly imageModel: typeof Image)
        
        getImage(data) {
            return this.imageModel(data)
        }
}
```
