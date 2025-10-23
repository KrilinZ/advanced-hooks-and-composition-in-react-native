---
readingTime:
  minutes: 1.184
  words: 296
fkglResult: 15.4
---

# 02.0 Introducción a useMemo



En React Native, algunas operaciones pueden ser costosas, como filtrar grandes listas o realizar cálculos complejos. Cada vez que un componente se renderiza, estas operaciones se vuelven a ejecutar, lo que puede afectar la fluidez de la aplicación. El hook **useMemo** permite memorizar el resultado de una función y solo recalcularlo cuando cambian sus dependencias. Esto evita cálculos innecesarios y mejora el rendimiento.



**¿Cuándo usar useMemo?**
- Cuando realizas **cálculos pesados** o filtras **listas grandes** que no deberían repetirse en cada render.  
- Cuando el **resultado calculado** se pasa como prop a componentes optimizados con `React.memo`.  
- Cuando necesitas **mantener la fluidez** en la interfaz, especialmente en listas o pantallas con mucha información.

**Ejemplo práctico:**

```javascript
import React, { useMemo } from 'react';
import { View, Text, FlatList } from 'react-native';

type Product = { id: number; name: string };

const ProductList: React.FC<{ products: Product[]; filter: string }> = ({ products, filter }) => {
  const filteredProducts = useMemo(() => {
    return products.filter(p =>
      p.name.toLowerCase().includes(filter.toLowerCase())
    );
  }, [products, filter]);

  return (
    <View style={{ padding: 20 }}>
      <FlatList
        data={filteredProducts}
        keyExtractor={(item) => item.id.toString()}
        renderItem={({ item }) => <Text>{item.name}</Text>}
      />
    </View>
  );
};

export default ProductList;
```

En este ejemplo, usamos `useMemo` para **filtrar una lista de productos** antes de renderizarla con `FlatList`. De esta forma, el filtrado solo se recalcula cuando cambian las dependencias (`products` o `filter`), evitando trabajo innecesario en cada renderizado.

💡 **Tip:** En React Native, optimizar operaciones con useMemo puede marcar la diferencia en el rendimiento de listas, pantallas con filtros o cálculos en tiempo real, manteniendo la experiencia fluida.





