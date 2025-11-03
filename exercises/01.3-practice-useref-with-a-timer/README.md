---
readingTime:
  minutes: 1.108
  words: 277
fkglResult: 16.73
---

# 01.3 Practice: Timer with useRef

In this practice, you will implement a **functional timer** that can be **started and stopped** correctly.  
You will use **`useRef`** to store the **interval ID**, avoiding the component re-rendering every time the counter increases.  This way, you will learn how `useRef` allows handling mutable values without affecting the interface.

**Place your code inside the [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) template** to run it and see how the timer works in real time.

```javascript
import React, { useRef, useState, useEffect } from 'react';
import { View, Text, Button } from 'react-native';

const Timer = () => {
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
};
```

### Reflect and answer:

In your own words, explain why **useRef** is the best choice to store the interval ID in this timer, instead of using **useState**.

```question eval="The user must explain that useRef allows storing mutable values that persist between renders without causing re-renders, which is ideal for interval IDs that do not directly affect the UI. useState would cause unnecessary re-renders every time the value changes." 
CORRECT: useRef stores values that do not cause re-renders, ideal for interval IDs.
CORRECT: useState would cause unnecessary re-renders when the ID changes.
CORRECT: useRef keeps the mutable value without affecting the UI.
INCORRECT: useRef automatically updates the UI.
INCORRECT: useState is better for values that do not change.
"""
