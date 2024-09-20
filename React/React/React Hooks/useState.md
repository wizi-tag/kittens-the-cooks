Возвращает значение с состоянием и функцию для его обновления.

```jsx
const [state, setState] = useState(initialState);
```

Во время первоначального рендеринга возвращаемое состояние `state` совпадает со значением, переданным в качестве первого аргумента `initialState`.

Функция `setState` используется для обновления состояния. Она принимает новое значение состояния и ставит в очередь повторный ререндер компонента.

```jsx
setState(newState);
```

> `setState` вызывает ререндер компонента.
> 

Если новое состояние вычисляется с использованием предыдущего состояния, вы можете передать функцию в `setState`. Функция получит предыдущее значение и вернет обновленное значение. Вот пример компонента счетчика, который использует обе формы `setState`:

```jsx
function Counter({initialCount}) {
  const [count, setCount] = useState(initialCount);
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </>);
}
```

Кнопки «+» и «-» используют функциональную форму, поскольку обновленное значение основано на предыдущем значении. А вот кнопка «Сброс» использует обычную форму, поскольку она всегда возвращает счетчик к исходному значению.

В качестве `initialValue` в `useState` может выступать также и функция. Но при вызове setState будет каждый раз происходить рендер.

```jsx
const initialCount() => {
	return 10;
}

function Counter() {
  const [count, setCount] = useState(initialCount());
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </>);
}
```

Для того чтобы оптимизировать данную ситуацию, можно функцию обернуть в callback и вернуть её из него. Эта callback функция один раз вычислит значение.

```jsx
const initialCount() => {
	return 10;
}

function Counter() {
  const [count, setCount] = useState(() => initialCount());
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </>);
}
```

### Заметки

> Два `useState` подряд вызовут один рендер.
> 

> Функция `setState` выполняется ассинхронно и чтобы отследить состояние `state` нужно обернуть `console.log(state)` в хук `useEffect()`.
> 

> Если мы передали в качестве `initialValue` объект. То при его изменении нужно понимать, что `setState` перезапишет его полностью. Как изменить состояние объекта правильно:
> 

```jsx
const [state, setState] = useState({
	title: 'i learning react...',
	name: 'vika'
});

const updateObject = () => {
	return setState(prev => {
		return {
			...prev,
			name: 'cat'
		}
	})
}
```