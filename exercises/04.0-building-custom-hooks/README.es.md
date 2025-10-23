---
readingTime:
  minutes: 1
  words: 225
fkglResult: 16.75
---

# 04.0 Introducción a los Hooks Personalizados



Los **hooks personalizados** son funciones que te permiten encapsular y reutilizar lógica que involucra hooks de React, manteniendo tus componentes limpios y enfocados en la interfaz.

### ¿Cuándo crear un hook personalizado?

- Cuando detectas **repetición de lógica** en varios componentes.
- Para manejar estados y efectos relacionados que pueden ser compartidos.

### Ejemplo práctico

Imagina que necesitas hacer llamadas a una API en diferentes partes de tu app. En lugar de repetir el código, creas un hook `useFetch` que maneja la solicitud, el estado de carga y los errores, facilitando la reutilización y mejorando la legibilidad.

---

![/.learn/assets/image-usefetch.png](/.learn/assets/image-usefetch.png)




