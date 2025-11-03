---
readingTime:
  minutes: 1
  words: 162
fkglResult: 16.26
---

# 01.1 useRef for DOM References

In React Native, **useRef** allows you to obtain a direct reference to a native component, which facilitates actions like focusing an input without needing to re-render the component.

#### Practical example:

```javascript
import { useRef } from 'react';
import { TextInput, Button, View } from 'react-native';

export default function LoginScreen() {
  const passwordRef = useRef(null);

  const focusPassword = () => {
    passwordRef.current?.focus();
  };

  return (
    <View>
      <TextInput placeholder="Email" onSubmitEditing={focusPassword} />
      <TextInput ref={passwordRef} placeholder="Password" secureTextEntry />
      <Button title="Go to password" onPress={focusPassword} />
    </View>
  );
}
```

### Practical challenge

**Practical activity:**  
- Use the [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) template to test this concept.  
- Implement a small form with **two text fields** and a **button**.  
- When the user presses the button, use **`useRef`** so that the focus automatically moves from the **first field** to the **second**.

💡 *Tip:* This practice will help you understand how `useRef` can control native components without causing re-renders.
