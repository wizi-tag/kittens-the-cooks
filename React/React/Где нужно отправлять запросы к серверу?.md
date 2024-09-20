В функциональных компонентах аналогом `componentDidMount` является хук `useEffect`. Внутри этого хука можно выполнять побочные эффекты, такие как запросы к серверу. Важно указать зависимости (второй аргумент хука) для того, чтобы запрос выполнялся только один раз при монтировании компонента или при изменении зависимости.

```jsx
import React, { useEffect, useState } from 'react';

const MyComponent = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []); // пустой массив зависимостей — запрос выполнится один раз при монтировании

  return <div>{data}</div>;
};
```