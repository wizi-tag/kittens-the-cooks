#react
#exam 
#pavlov

> *Дмитрий Павлов*
> *24.09.24*
---

Как тебе опыт с этой библиотекой, что тебе показалось необычным / интересным?
Как начать приложение на React?
Какое приемущество у React по стравнению с другими фреймворками?  (коммунити)
Как выглядит реакт? Какие есть основные части? Как с ним работать?
Что нужно кроме реакта для запуска реакт приложения? (какие библиотеки)
Что делает ReactDOM?
Как выглядят React компоненты?
Остались ли у нас случаи когда нам нужны классовые компоненты?
Какого формата ошибки ловятся при помощи ComponentDidCatch?
Что принимает метод ComponentDidCatch?

```tsx
const ComponentA = () => {
	console.log("a");
	return <img src="example.png"/>;
}

const ComponentB = () => {
	console.log("b");
	return <ComponentA />;
};

const ComponentC = () => {
	console.log("c");
	return <ComponentB />;
};

export default function App() {
  return <ComponentC />;
};
```

// потом добавление useState & useEffect
```tsx
import { useEffect } from "react";

const ComponentA = () => {
  console.log("a");
  useEffect(() => console.log("effectA"), []);
  return <img src="example.png" />;
};

const ComponentB = () => {
  console.log("b");
  useEffect(() => console.log("effectB"), []);
  return <ComponentA />;
};

const ComponentC = () => {
  console.log("c");
  useEffect(() => console.log("effectC"), []);
  return <ComponentB />;
};

export default function App() {
  return <ComponentC />;
};
```

Что будет раньше setState или console.log?

Как предотвратить перерендер компонентов?
Какие методы жизненного цикла знаешь?
Знаешь useLayoutEffect? Когда он вызывается?
Как получить пропсы в классовом компоненте?

Для чего нужен V-DOM?
Какие приемущества у V-DOM помимо частичной перерисовки интерфейса?
Что такое batching?
Знаешь какие-нибудь новые хуки?
Какие нововведения React 19 тебя ещё заинтересовали?
Зачем используется UseId? Зачем нужны Id которые будут сбрасываться каждый рендер? 
*(для управления неконтроллируемыми инпутами)*
Для чего нам нужен useRef?
Как прокинуть ref дочернему компоненту?
Как посчитать количество перерендеров компонента?

Когда вызывается cleanUp функция у useEffect?
Что такое порталы?

Рекомендуется использовать реакт с фреймворком

Какие есть способы оптимизации React приложений?
Какие есть хуки для мемоизации?
В чём разница useMemo и useCallback?
Как часто пересоздаются функции?

Что такое Fragment?
Можем ли мы задать ему key?
Что такое key?

Зачем нам нужен Redux если есть useContext?