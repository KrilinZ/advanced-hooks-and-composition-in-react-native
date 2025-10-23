---
readingTime:
  minutes: 1.184
  words: 296
fkglResult: 15.4
---

# 02.0 Introduction to useMemo

In React Native, some operations can be costly, such as filtering large lists or performing complex calculations. Every time a component renders, these operations are executed again, which can affect the app's smoothness. The **useMemo** hook allows you to memoize the result of a function and only recalculate it when its dependencies change. This avoids unnecessary calculations and improves performance.

**When to use useMemo?**
- When performing **heavy calculations** or filtering **large lists** that shouldn't be repeated on every render.
- When the **calculated result** is passed as a prop to components optimized with `React.memo`.
- When you need to **maintain smoothness** in the interface, especially in lists or screens with a lot of information.

**Practical example:**

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

In this example, we use `useMemo` to **filter a list of products** before rendering it with `FlatList`. This way, the filtering is only recalculated when the dependencies (`products` or `filter`) change, avoiding unnecessary work on each render.

💡 **Tip:** In React Native, optimizing operations with useMemo can make a difference in the performance of lists, screens with filters, or real-time calculations, maintaining a smooth experience.