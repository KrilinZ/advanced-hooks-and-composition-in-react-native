---
readingTime:
  minutes: 1.008
  words: 252
fkglResult: 13.28
---

# 01.0 Understanding the Basics of useRef

In React Native, **useRef** is a hook that allows storing mutable values that persist between renders without causing re-renders. Unlike **useState**, which triggers a UI update every time its value changes, **useRef** is ideal for handling references to native components or values that do not need to be reflected in the UI.

**When to use useRef?**
- To directly access native components, such as focusing an input field.
- To store changing values (like interval IDs) without affecting performance or causing renders.

**Practical example:**

```javascript
const passwordRef = useRef(null);
const focusPassword = () => passwordRef.current.focus();
```

In conclusion:

- **useRef** does not cause component re-renders.  
- It is ideal for handling **references** or **internal mutable values** that should not affect the UI.  
- In **React Native**, it is mainly used to **interact with native components** like `TextInput`, `ScrollView`, or `FlatList`.