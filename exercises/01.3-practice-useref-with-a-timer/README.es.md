---
readingTime:
  minutes: 1.108
  words: 277
fkglResult: 16.73
---

# 01.3 Práctica: Temporizador con useRef



En esta práctica, implementarás un **temporizador funcional** que puede **iniciarse y detenerse** correctamente.  
Utilizarás **`useRef`** para guardar el **ID del intervalo**, evitando que el componente se re-renderice cada vez que el contador aumenta.  De esta forma, aprenderás cómo `useRef` permite manejar valores mutables sin afectar la interfaz.  

**Coloca tu código dentro de la plantilla [`react-native-hello`](https://github.com/4GeeksAcademy/react-native-hello)** para ejecutarlo y observar cómo el temporizador funciona en tiempo real.

```javascript
import React, { useRef, useState, useEffect } from 'react';
import { View, Text, Button } from 'react-native';

const Timer = () => {
  const intervalRef = useRef(null);
  const [seconds, setSeconds] = useState(0);

  const startTimer = () => {
    if (intervalRef.current) return; // Evita múltiples intervalos
    intervalRef.current = setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);
  };

  const stopTimer = () => {
    clearInterval(intervalRef.current);
    intervalRef.current = null;
  };

  useEffect(() => {
    return () => stopTimer(); // Limpieza al desmontar
  }, []);

  return (
    <View>
      <Text>{seconds} segundos</Text>
      <Button title="Iniciar" onPress={startTimer} />
      <Button title="Detener" onPress={stopTimer} />
    </View>
  );
};
```

### Reflexiona y responde:

En tus propias palabras, explica por qué **useRef** es la mejor opción para almacenar el ID del intervalo en este temporizador, en lugar de usar **useState**.

```question eval="El usuario debe explicar que useRef permite almacenar valores mutables que persisten entre renders sin causar re-renderizados, lo que es ideal para IDs de intervalos que no afectan la UI directamente. useState provocaría re-renderizados innecesarios cada vez que cambia el valor." 
CORRECT: useRef almacena valores que no causan re-renderizados, ideal para IDs de intervalos.
CORRECT: useState causaría re-renderizados innecesarios al cambiar el ID.
CORRECT: useRef mantiene el valor mutable sin afectar la UI.
INCORRECT: useRef actualiza la UI automáticamente.
INCORRECT: useState es mejor para valores que no cambian.
"""
