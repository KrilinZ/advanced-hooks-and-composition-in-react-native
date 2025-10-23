---
readingTime:
  minutes: 1
  words: 233
fkglResult: 14.84
---

# 03.1 useCallback para la Optimización de Funciones



En React, **cada render crea nuevas funciones** definidas dentro del componente.  Si pasas esas funciones a **hijos memorizados** con `React.memo`, pueden **re-renderizarse innecesariamente** porque la **referencia** de la función cambia.

`useCallback` **memoriza** la función y **mantiene su referencia estable** entre renders (mientras no cambien sus dependencias). Así evitas renders extra y mejoras el rendimiento.



**Ejemplo práctico:**

```javascript
import React, { useCallback, useMemo } from 'react';
import { FlatList, Text } from 'react-native';

type Item = { id: string; name: string };
const data: Item[] = [/* ... */];

const List: React.FC = () => {
  // Opcional: memorizamos datos/derivados si hiciera falta
  const items = useMemo(() => data, []);

  // `renderItem` estable: evita re-renders de celdas memorizadas
  const renderItem = useCallback(({ item }: { item: Item }) => {
    return <Text>{item.name}</Text>;
  }, []);

  const keyExtractor = useCallback((item: Item) => item.id, []);

  return (
    <FlatList
      data={items}
      renderItem={renderItem}
      keyExtractor={keyExtractor}
    />
  );
};
```

### Cuándo usarlo
- Pasas **callbacks** a componentes hijos envueltos en `React.memo`.
- Pasas callbacks a **listas** (`FlatList`/`SectionList`) como `renderItem` o `keyExtractor`.
- El callback es **costoso de crear** o provoca cálculos en los hijos.

> No lo uses por defecto en todos lados, memorizar también tiene un coste. Úsalo cuando veas renders innecesarios.

**Resumen:** useCallback mantiene estable la referencia de tus funciones. Úsalo cuando esa estabilidad evita re-renderizados en hijos memorizados o listas.



