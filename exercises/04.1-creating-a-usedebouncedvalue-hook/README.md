---
readingTime:
  minutes: 1.304
  words: 326
fkglResult: 9.96
---

# 04.1 Creating a useDebouncedValue Hook

Create a **`useDebouncedValue`** hook that delays the propagation of a value until the user stops typing for *X* milliseconds.

It is useful for:
- live searches,
- expensive validations,
- filtering large lists (avoids recalculating on every keystroke).

### Hook skeleton

```javascript
import { useEffect, useState } from 'react';

export function useDebouncedValue<T>(value: T, delay: number): T {
  const [debounced, setDebounced] = useState<T>(value);

  useEffect(() => {
    const id = setTimeout(() => setDebounced(value), delay);
    return () => clearTimeout(id);
  }, [value, delay]);

  return debounced;
}
```

---

### Search screen

```javascript
import React, { useMemo, useState } from 'react';
import { View, TextInput, FlatList, Text, StyleSheet } from 'react-native';
import { useDebouncedValue } from './useDebouncedValue';

type Product = { id: string; name: string };
const PRODUCTS: Product[] = [
  { id: '1', name: 'Keyboard' },
  { id: '2', name: 'Mouse' },
  { id: '3', name: 'Monitor' },
  { id: '4', name: 'Camera' },
  { id: '5', name: 'Microphone' },
];

export default function SearchScreen() {
  const [query, setQuery] = useState('');
  const debouncedQuery = useDebouncedValue(query, 350);

  const filtered = useMemo(() => {
    const q = debouncedQuery.trim().toLowerCase();
    return q.length === 0
      ? PRODUCTS
      : PRODUCTS.filter(p => p.name.toLowerCase().includes(q));
  }, [debouncedQuery]);

  return (
    <View style={styles.container}>
      <TextInput
        style={styles.input}
        placeholder="Type to search..."
        value={query}
        onChangeText={setQuery}
      />
      <FlatList
        data={filtered}
        keyExtractor={item => item.id}
        renderItem={({ item }) => <Text style={styles.item}>{item.name}</Text>}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: { padding: 16, gap: 12 },
  input: { borderWidth: 1, borderColor: '#ccc', borderRadius: 8, padding: 10 },
  item: { paddingVertical: 8, fontSize: 16 },
});
```

Let's get coding!