---
readingTime:
  minutes: 1.452
  words: 363
fkglResult: 14.43
---

# 01.2 useRef para Valores Mutables



En **React Native**, el hook `useRef` no solo se usa para acceder a componentes nativos, sino también para **almacenar valores que cambian** sin provocar re-renderizados. Esto resulta muy útil para manejar elementos como **temporizadores, intervalos o identificadores**, donde no necesitas actualizar la interfaz cada vez que cambian.

#### Ejemplo práctico: Temporizador con useRef

```javascript
import { useRef, useEffect, useState } from 'react';
import { View, Text, Button } from 'react-native';

function Temporizador() {
  const intervalRef = useRef(null);
  const [segundos, setSegundos] = useState(0);

  const iniciarTemporizador = () => {
    if (intervalRef.current) return; // Evita múltiples intervalos
    intervalRef.current = setInterval(() => {
      setSegundos(s => s + 1);
    }, 1000);
  };

  const detenerTemporizador = () => {
    clearInterval(intervalRef.current);
    intervalRef.current = null;
  };

  useEffect(() => {
    return () => detenerTemporizador(); // Limpieza al desmontar
  }, []);

  return (
    <View>
      <Text>{segundos} segundos</Text>
      <Button title="Iniciar" onPress={iniciarTemporizador} />
      <Button title="Detener" onPress={detenerTemporizador} />
    </View>
  );
}
```

**Diferencia clave:**
- **useState:** Cambiar el valor provoca re-render y actualiza la UI.
- **useRef:** Cambiar el valor no provoca re-render; es útil para valores internos que no afectan la interfaz.

---







