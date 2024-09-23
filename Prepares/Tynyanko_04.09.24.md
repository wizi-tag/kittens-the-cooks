#node-nest
#prepare 

Сервер с информацией о сервере
```js
const http = require('node:http');
const process = require('node:process');
const os = require('node:os');
const fs = require('node:fs');

const srv = http.createServer((req, res) => {
	if (req.url.split('/')[1] === 'uptime') {
		res.end(process.uptime()+'');
	} else if (req.url.split('/')[1] === 'free-mem') {
		res.end(os.freemem()+'');
	} else if (req.url.split('/')[1] === 'resourses') {
		res.end(process.memoryUsage()+'');
	} else if (req.url.split('/')[1] === 'file') {
		const rs = fs.createReadStream('bigFile.txt');
		rs.pipe(res);
	} else if (req.url.split('/')[1] === 'greet') {
		req.on('data', (data) => {
			data = JSON.parse(data.toString());
			res.end(`Hello ${data[Object.keys(data)[0]]}`);
		})
	}
});

const PORT = 3000;

srv.listen(PORT, () => {
	console.log('listen on PORT: ', PORT)
});
```

``