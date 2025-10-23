---
readingTime:
  minutes: 1
  words: 216
fkglResult: 13.25
---

# 03.0 ¿Qué es useCallback?

El objetivo de esta lección es entender qué es **useCallback** y cuándo es útil en React Native.

**useCallback** es un hook que memoriza funciones para evitar que se creen de nuevo en cada renderizado del componente. Esto es especialmente importante cuando pasamos funciones como props a componentes hijos que están optimizados con **React.memo**. Sin **useCallback**, cada render del componente padre genera una nueva función, lo que puede causar re-renderizados innecesarios en los hijos.

### ¿Cuándo usar useCallback?

- Cuando pasas funciones a componentes hijos memorizados con **React.memo**.
- Para evitar recrear funciones en renders que no afectan la lógica de la interfaz.

### Reflexiona y responde:

¿Cuál es la ventaja principal de usar **useCallback** en un componente React? Explica con tus propias palabras.

```question eval="El usuario debe explicar que useCallback ayuda a evitar la recreación innecesaria de funciones en cada render, mejorando el rendimiento y evitando re-renderizados innecesarios en componentes hijos memorizados."
CORRECT: useCallback evita que se creen nuevas funciones en cada render, lo que mejora el rendimiento.
CORRECT: Permite que los componentes hijos memorizados no se re-rendericen innecesariamente.
INCORRECT: useCallback crea nuevas funciones en cada render para actualizar la UI.
INCORRECT: useCallback se usa para manejar estados en React.
CORRECT: Memoriza funciones para mantener la misma referencia entre renders.
```
