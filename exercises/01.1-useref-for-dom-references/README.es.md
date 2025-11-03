---
readingTime:
  minutes: 1
  words: 162
fkglResult: 16.26
---

# 01.1 useRef para Referencias al DOM



En React Native, **useRef** permite obtener una referencia directa a un componente nativo, lo que facilita acciones como enfocar un input sin necesidad de re-renderizar el componente.

#### Ejemplo práctico:

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
      <TextInput ref={passwordRef} placeholder="Contraseña" secureTextEntry />
      <Button title="Ir a contraseña" onPress={focusPassword} />
    </View>
  );
}
```

### Desafío práctico

**Actividad práctica:**  
- Usa la plantilla [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) para poner a prueba este concepto.  
- Implementa un pequeño formulario con **dos campos de texto** y un **botón**.  
- Cuando el usuario presione el botón, utiliza **`useRef`** para que el foco pase automáticamente del **primer campo** al **segundo**.  

💡 *Tip:* Esta práctica te ayudará a entender cómo `useRef` puede controlar componentes nativos sin provocar re-renderizados.

