---
readingTime:
  minutes: 1
  words: 236
fkglResult: 13.42
---

# 03.2 Práctica: Optimización con useCallback



Cuando pasas funciones como props a componentes hijos memorizados, cada render crea una nueva función, lo que puede causar que el hijo se re-renderice sin necesidad. **useCallback** memoriza la función y mantiene su referencia estable mientras sus dependencias no cambien.

### Actividad práctica:

1. Crea un componente padre con un estado y una función que modifique ese estado.
2. Usa **useCallback** para memorizar esa función.
3. Pasa la función memorizada como prop a un componente hijo memorizado con **React.memo**.
4. Observa que el componente hijo solo se re-renderiza cuando es necesario.

![GENERATING: Diagrama que muestra un componente padre pasando una función memorizada con useCallback a un componente hijo memorizado con React.memo, con flechas que indican el flujo de props y anotaciones que resaltan la estabilidad de la referencia de la función y la prevención de re-renderizados innecesarios](/.learn/assets/a5n4en2vmbf)







