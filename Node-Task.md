#node-nest 
#tasks 

На сервере хранится файл `users.csv` в формате:
```csv
id,username,email,phone
1,johnee,john@doe.com,8-888-888
2,_sarah_,sarah@con.fr,9-999-999
```
Реализовать сервер который позволит добавлять и редактировать пользователей.
```js
// Add user
POST /users/
{
	username: "",
	email: "",
	phone: "",
}
```

```js
// Edit user
PATCH /users/:id/
{
	username: "",
	email: "",
	phone: "",
}
```

```js
// Get users
GET /users/

// Get user
GET /users/:id/
```
---
```js
const http = require('http');
const path = require('path');
const fs = require('fs');
const os = require('os');

const PORT = 3000;
const pathFile = './users.csv';

const updateUser = (user, editParams, indexName, indexLogin) => {
  const userField = user.split(/, /);
  console.log('1. userField = ', userField);
  
  editParams.forEach(element => {
    const key = element.split('=')[0];
    const value = element.split('=')[1];

    if (key === 'name') {
      userField[indexName] = value
    } else {
      userField[indexLogin] = value
    }
    console.log('2. userField = ', userField);
  });

  return userField.join(', ').trim();
}

const searchAndUpdateUser = (users, userId, queryParams) => {
  const middle = Math.floor(users.length/2);
  let i = userId <= middle ? 1 : middle;

  const headrs = users[0].split(/, /);
  const indexName = headrs.indexOf('name');
  const indexLogin = headrs.indexOf('login');

  for (i; i < middle; i++) {
    if(+users[i][0] === +userId) {
      users[i] = updateUser(users[i], queryParams, indexName, indexLogin)
      console.log('newUser = ', users[i]);
    }
  }
  
  return users.join(`${os.EOL}`);
}

const server = http.createServer();
server.on('request', (req, res) => {
  const reqSplit = req.url.split(/[\/?&]/);
  console.log('req.url = ', req.url);
  console.log('reqSplit = ', reqSplit);
  if (req.method === 'PATCH' && reqSplit[1] === 'users') {
    const queryParams = reqSplit.slice(3);
    console.log('queryParams = ', queryParams);
    const userId = reqSplit[2];
    console.log('id = ', userId);

    fs.promises.access(pathFile).then(() => {
      console.log('Файл существует');
      fs.readFile(pathFile, 'utf8', (err, data) => {
        if (err) {
          res.writeHead(500, { 'Content-Type': 'text/plain'});
          res.end('Произошла ошибка чтения файла');
        }
  
        const users = data.split(`${os.EOL}`);
        console.log(users);
  
        const newData = searchAndUpdateUser(users, userId, queryParams);
        console.log('newData = ', newData);
        
        fs.writeFile(pathFile, newData, 'utf8', (err) => {
          if (err) {
            res.writeHead(500, { 'Content-Type': 'text/plain'});
            res.end('Произошла ошибка записи файла');
          }
        });
  
        res.writeHead(200, { 'Content-Type': 'text/plain'});
        res.end('Данные изменены');
      });
    }).catch(() => {
      console.log('Не удалось найти файл');
      res.writeHead(404, { 'Content-Type': 'text/plain'});
      res.end('Файл не найден');
    });
  }
})

server.listen(
	PORT, 
	() => console.log(`Server running on http://localhost:${PORT}`)
)
```