---
readingTime:
  minutes: 1.008
  words: 252
fkglResult: 13.28
---

# 01.0 Comprendiendo los Fundamentos de useRef



En React Native, **useRef** es un hook que permite almacenar valores mutables que persisten entre renders sin causar re-renderizados. A diferencia de **useState**, que provoca una actualización de la interfaz cada vez que cambia su valor, **useRef** es ideal para manejar referencias a componentes nativos o valores que no necesitan reflejarse en la UI.

**¿Cuándo usar useRef?**
- Para acceder directamente a componentes nativos, como enfocar un campo de entrada.
- Para guardar valores que cambian (como IDs de intervalos) sin afectar el rendimiento ni provocar renders.

**Ejemplo práctico:**

```javascript
const passwordRef = useRef(null);
const focusPassword = () => passwordRef.current.focus();
``` 

En conclusión:

- **useRef** no provoca re-renderizados del componente.  
- Es ideal para manejar **referencias** o **valores mutables internos** que no deben afectar la UI.  
- En **React Native**, se usa principalmente para **interactuar con componentes nativos** como `TextInput`, `ScrollView` o `FlatList`.












