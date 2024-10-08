**`useCallback`** - это хук React, который позволяет кэшировать определение функции между повторными рендерингами.

### **Возвращаемое значение**

При первоначальном рендере `useCallback` возвращает переданную вами функцию `fn`.

При последующих рендерах она либо вернет уже сохраненную функцию `fn` из последнего рендера (если зависимости не изменились), либо вернет функцию `fn`, которую вы передали во время этого рендера.

### Чем отличается от useMemo в который мы  тоже можем обернуть функцию?

1. **Назначение**:
    - **`useMemo`**: Используется для мемоизации **результата вычисления функции**. То есть, он сохраняет (кэширует) значение, возвращаемое функцией, чтобы не пересчитывать его на каждом рендере, если зависимости не изменились.
    - **`useCallback`**: Используется для мемоизации **самой функции**. Он возвращает ту же самую функцию между рендерами, если зависимости не изменились.
2. **Возвращаемое значение**:
    - **`useMemo`**: Возвращает мемоизированное значение (результат вычисления).
    - **`useCallback`**: Возвращает мемоизированную функцию.

> Нет смысла оборачивать в него функцию просто так, это не оптимизирует ничего. useCallback предназначен для оборачивания функций, которые передаются в дочерний компонент.
> 

> Если функция используется в качестве зависимостей, к примеру, в useEffect. Необходимо её так же обернуть в useCallback.
> 

![image.png](React/React/React%20Hooks/useCallback_img/image.png)