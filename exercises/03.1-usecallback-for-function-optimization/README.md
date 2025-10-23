---
readingTime:
  minutes: 1
  words: 233
fkglResult: 14.84
---

# 03.1 useCallback for Function Optimization

In React, **each render creates new functions** defined inside the component. If you pass those functions to **memoized children** with `React.memo`, they can **re-render unnecessarily** because the **function reference changes**.

`useCallback` **memoizes** the function and **keeps its reference stable** between renders (as long as its dependencies don't change). This way, you avoid extra renders and improve performance.


**Practical example:**

```javascript
import React, { useCallback, useMemo } from 'react';
import { FlatList, Text } from 'react-native';

type Item = { id: string; name: string };
const data: Item[] = [/* ... */];

const List: React.FC = () => {
  // Optional: memoize data/derived values if needed
  const items = useMemo(() => data, []);

  // Stable `renderItem`: prevents re-renders of memoized cells
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

### When to use it
- You pass **callbacks** to child components wrapped in `React.memo`.
- You pass callbacks to **lists** (`FlatList`/`SectionList`) as `renderItem` or `keyExtractor`.
- The callback is **expensive to create** or causes calculations in children.

> Don't use it by default everywhere; memoizing also has a cost. Use it when you see unnecessary renders.

**Summary:** useCallback keeps your function references stable. Use it when that stability prevents re-renders in memoized children or lists.

