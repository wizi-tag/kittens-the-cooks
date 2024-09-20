`react-router` — это библиотека для управления маршрутизацией в приложениях на React. Она позволяет создавать одностраничные приложения (SPA), в которых различные URL-адреса отображают разные компоненты или представления, не перезагружая страницу.

### Основные функции `react-router`:

1. **Маршрутизация:** Определение, какой компонент или представление отображать в зависимости от URL.
2. **Навигация:** Позволяет пользователям перемещаться по приложению, изменяя URL и отображая соответствующие компоненты.
3. **Поддержка вложенных маршрутов:** Позволяет создавать сложные интерфейсы с несколькими уровнями маршрутизации.
4. **Динамические маршруты:** Позволяет передавать параметры через URL для динамического отображения данных.
5. **Переходы и редиректы:** Управление навигацией и перенаправлением на другие страницы или маршруты.

### Установка `react-router`

Для начала работы с `react-router`, вам нужно установить его зависимости. Для React версии 18 и выше используйте `react-router-dom`:

```bash
npm install react-router-dom
```

### Основные компоненты и функции `react-router`

1. **`BrowserRouter`**: Обертка для вашего приложения, которая использует HTML5 History API для управления URL-адресами.
2. **`Routes`**: Компонент, который содержит определение маршрутов для вашего приложения.
3. **`Route`**: Определяет отдельный маршрут, связывая путь URL с компонентом.
4. **`Link`**: Компонент для создания ссылок, которые управляют навигацией внутри приложения.
5. **`Navigate`**: Компонент для программной навигации и перенаправлений.
6. **`Outlet`**: Используется для рендеринга вложенных маршрутов внутри родительского маршрута.

### Пример использования

Вот базовый пример настройки маршрутизации в React приложении с использованием `react-router-dom`:

1. **Создайте структуру компонентов**

```jsx
// Home.jsx
import React from 'react';

const Home = () => {
  return <h1>Home Page</h1>;
};

export default Home;

// About.jsx
import React from 'react';

const About = () => {
  return <h1>About Page</h1>;
};

export default About;

// NotFound.jsx
import React from 'react';

const NotFound = () => {
  return <h1>404 - Page Not Found</h1>;
};

export default NotFound;
```

1. **Настройте маршрутизацию**

```jsx
// App.jsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import About from './About';
import NotFound from './NotFound';

const App = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/about">About</Link></li>
        </ul>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<NotFound />} /> {/* 404 Not Found */}
      </Routes>
    </Router>
  );
};

export default App;
```