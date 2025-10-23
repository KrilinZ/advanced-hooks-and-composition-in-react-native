---
readingTime:
  minutes: 1.452
  words: 363
fkglResult: 14.43
---

# 01.2 useRef for Mutable Values

In **React Native**, the `useRef` hook is not only used to access native components but also to **store values that change** without causing re-renders. This is very useful for handling elements like **timers, intervals, or identifiers**, where you don't need to update the interface every time they change.

#### Practical Example: Timer with useRef

```javascript
import { useRef, useEffect, useState } from 'react';
import { View, Text, Button } from 'react-native';

function Timer() {
  const intervalRef = useRef(null);
  const [seconds, setSeconds] = useState(0);

  const startTimer = () => {
    if (intervalRef.current) return; // Prevent multiple intervals
    intervalRef.current = setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);
  };

  const stopTimer = () => {
    clearInterval(intervalRef.current);
    intervalRef.current = null;
  };

  useEffect(() => {
    return () => stopTimer(); // Cleanup on unmount
  }, []);

  return (
    <View>
      <Text>{seconds} seconds</Text>
      <Button title="Start" onPress={startTimer} />
      <Button title="Stop" onPress={stopTimer} />
    </View>
  );
}
```

**Key difference:**
- **useState:** Changing the value causes a re-render and updates the UI.
- **useRef:** Changing the value does not cause a re-render; it is useful for internal values that do not affect the interface.

---