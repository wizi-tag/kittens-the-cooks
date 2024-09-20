`useContext` — это хук в React, который позволяет получать доступ к данным, хранящимся в контексте, в любом компоненте и на любом уровне вложенности, без необходимости передавать эти данные через пропсы. Контекст в React используется для обмена данными между компонентами без необходимости явно передавать пропсы на каждом уровне.

### Основные шаги использования `useContext`:

1. **Создание контекста**.
2. **Предоставление (провайдинг) данных контекста**.
3. **Использование контекста в компонентах с помощью `useContext`**.

### 1. Создание контекста:

Для начала создадим контекст с помощью `React.createContext`:

```jsx
import React, { createContext, useState } from 'react';

// Создаем контекст с дефолтным значением (например, 'light' для светлой темы)
const ThemeContext = createContext('light');
```

### 2. Провайдинг контекста:

Далее создадим компонент `ThemeProvider`, который будет оборачивать другие компоненты и предоставлять им данные контекста:

```jsx
const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme(prevTheme => prevTheme === 'light' ? 'dark' : 'light');
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}
```

В этом примере мы используем `ThemeContext.Provider` для предоставления значений `theme` и `toggleTheme` всем дочерним компонентам.

### 3. Использование `useContext` в компонентах:

Теперь в любом компоненте, который находится внутри `ThemeProvider`, мы можем получить доступ к данным контекста с помощью `useContext`.

```jsx
import React, { useContext } from 'react';

const ThemedButton = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <button
      onClick={toggleTheme}
      style={{
        backgroundColor: theme === 'light' ? '#fff' : '#333',
        color: theme === 'light' ? '#000' : '#fff',
      }}
    >
      Переключить тему
    </button>
  );
}
```

### Полный пример использования:

```jsx
import React, { createContext, useContext, useState } from 'react';

// Создаем контекст
const ThemeContext = createContext('light');

// Компонент ThemeProvider, который предоставляет контекст
const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme(prevTheme => prevTheme === 'light' ? 'dark' : 'light');
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

// Компонент, который использует контекст
const ThemedButton = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <button
      onClick={toggleTheme}
      style={{
        backgroundColor: theme === 'light' ? '#fff' : '#333',
        color: theme === 'light' ? '#000' : '#fff',
      }}
    >
      Переключить тему
    </button>
  );
}

// Пример использования ThemeProvider и ThemedButton в приложении
const App = () => {
  return (
    <ThemeProvider>
      <ThemedButton />
    </ThemeProvider>
  );
}

export default App;
```