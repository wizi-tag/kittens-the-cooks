#prepare 
#node-nest 

Кодировка в строки base64
```js
const msg = 'Hello';
const result = 'SGVsbG8='

const fn = (msg) => {
	const buf = Buffer.from(msg, 'utf8');
	return buf.toString('base64');
}

console.log(fn(msg) === result)
```

Запись в середину файла
```js
const fs = require('fs');
const os = require('os');

const readStream = fs.createReadStream('./bigFile');
let result = '';

readStream.on('data', (chunk) => {
	result += chunk.toString('utf8');
});

readStream.on('end', () => {
	const rows = result.split(os.EOL)
	rows.splice(
		Math.trunc(rows.length/2), 
		0, 
		'!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!'
	);
	const newResult = rows.join(os.EOL);
	fs.writeFileSync('./bigFile', newResult, 'utf8', () => {});
})
```

Прокси сервер
```js
const http = require('http');
const https = require('https');

const PORT = 3000;

const getTodos = (id = '', userRes) => {
	const todosId = Number(id) ? `/${id}` : ''
	https.get(`https://jsonplaceholder.typicode.com/todos${id}`, (res) => {
		res.pipe(userRes)
	});
}

const server = http.createServer((req, res) => {
	if (req.method === 'GET') {
		const id = req.url.split('/').pop();
		getTodos(id, res);
	}
})

server.listen(PORT, () => console.log(`Server running on PORT ${PORT}$`));
```
