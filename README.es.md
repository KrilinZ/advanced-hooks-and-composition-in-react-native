<!-- hide -->
<div align="center">

# Advanced Hooks and Composition in React Native with TypeScript

[![Certificado por 4Geeks](https://img.shields.io/badge/4Geeks-certified-2563eb)](https://4geeks.com/es/interactive-exercise/advanced-hooks-and-composition-in-react-native--es)
[![Hecho con LearnPack](https://img.shields.io/badge/LearnPack-tutorial-2563eb)](https://4geeks.com/docs/learnpack)
[![Plantilla react-native-cli-hello](https://img.shields.io/badge/Plantilla-react--native--cli--hello-fb5a1f)](https://github.com/breatheco-de/react-native-cli-hello)

</div>
<!-- endhide -->

Este tutorial interactivo enseña hooks avanzados de React Native con TypeScript en 17 lecciones breves, estimadas en 60 minutos. Practicas `useRef` para referencias a componentes nativos y para IDs de intervalos, `useMemo` para filtrar una lista de productos, `useCallback` para mantener estable el `renderItem` de un `FlatList`, y hooks propios como `useDebouncedValue` y `useFetch`. Incluye 6 retos de código y 4 cuestionarios con 11 preguntas; el código que escribes se ejecuta en la plantilla `react-native-cli-hello`.

<!-- hide -->
## 📋 Ficha del tutorial

- **Dificultad**: principiante (`"difficulty": "beginner"` en `learn.json`)
- **Duración estimada**: 60 minutos. Las 17 lecciones declaran unos 18 minutos de lectura y cerca de 3.800 palabras
- **Lecciones**: 17 carpetas dentro de `exercises/`, numeradas del `00.0` al `04.3`
- **Práctica**: 6 retos para escribir tú, 4 cuestionarios de opción múltiple (11 preguntas) y 2 preguntas de respuesta abierta
- **Tecnologías**: React Native, TypeScript, desarrollo móvil
- **Dónde se ejecuta el código**: la plantilla [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello), que vive en otro repositorio
- **Corrección**: no hay corrección automática — este paquete no incluye ficheros de test
- **Idiomas**: [English](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/blob/HEAD/README.md) · [Español](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/blob/HEAD/README.es.md)
<!-- endhide -->

## 🎯 ¿Qué vas a aprender?

- Cómo [`useRef`](https://react.dev/reference/react/useRef) guarda un valor mutable que sobrevive a los renders **sin provocar ninguno**, y por qué ese es el sitio natural para el ID de un intervalo.
- Cómo apuntar una referencia a un componente nativo y llamar a sus métodos, por ejemplo saltando el foco al siguiente `TextInput` con `passwordRef.current?.focus()`.
- Cómo [`useMemo`](https://react.dev/reference/react/useMemo) cachea el resultado de un cálculo costoso y solo lo recalcula cuando cambian sus dependencias, manteniendo fluido un [`FlatList`](https://reactnative.dev/docs/flatlist) filtrado mientras el usuario escribe.
- Cómo [`useCallback`](https://react.dev/reference/react/useCallback) mantiene estable la referencia de una función entre renders, de modo que los hijos envueltos en [`React.memo`](https://react.dev/reference/react/memo) y props de lista como `renderItem` o `keyExtractor` dejen de redibujarse sin motivo.
- Por qué memorizar no es gratis, y cuál es la señal que indica que toca hacerlo: estás viendo renders que no cambian nada en pantalla.
- Cómo sacar la lógica repetida a un hook propio, tipado con [genéricos](https://www.typescriptlang.org/docs/handbook/2/generics.html) de TypeScript para que `useDebouncedValue<T>(value, delay)` devuelva el mismo tipo que recibe.
- Cómo un hook de datos devuelve `{ data, loading, error }` y permite que varias pantallas compartan un mismo ciclo de petición en vez de copiar llamadas a `fetch`.

![Diagrama de la lección 04.0: tres cajas etiquetadas Component A, Component B y Component C apuntan a una única caja azul useFetch, que a su vez se ramifica en los estados loading, data y error y hacia una caja API Call, bajo el rótulo Reuse](https://raw.githubusercontent.com/breatheco-de/advanced-hooks-and-composition-in-react-native/main/.learn/assets/image-usefetch.png)

## 👀 ¿Qué vas a construir?

Las 17 lecciones están agrupadas en cinco bloques. Cada lección es un fichero Markdown: ocho traen un fragmento de código en TypeScript o JavaScript, cuatro son cuestionarios y el resto son teoría o el enunciado de algo que te toca escribir a ti:

- **`00.0` Bienvenida (1 lección)** — una introducción de un minuto que presenta lo que viene: `useRef`, `useMemo`, `useCallback` y la reutilización de lógica entre componentes.
- **`01.0` a `01.4` — useRef (5 lecciones)** — la diferencia entre una referencia y el estado, referencias a componentes nativos, referencias con valores mutables, un temporizador con Start y Stop cuyo ID de `setInterval` vive en una ref, y un cuestionario de 3 preguntas.
- **`02.0`, `02.2`, `02.3` — useMemo (3 lecciones)** — cuándo compensa cachear un cálculo, un componente `ProductList` que escribes tú, y un cuestionario de 3 preguntas. La numeración de carpetas salta del `02.0` al `02.2`: no existe el `02.1`.
- **`03.0` a `03.3` — useCallback (4 lecciones)** — qué tiene que ver la identidad de una función con los renders, `renderItem` y `keyExtractor` estables para un `FlatList`, un ejercicio de padre e hijo con `React.memo`, y un cuestionario de 2 preguntas.
- **`04.0` a `04.3` — Hooks propios (4 lecciones)** — cuándo conviene extraer un hook, un `useDebouncedValue` construido desde cero, un recorrido por `useFetch` con un diagrama de secuencia del ciclo de la petición, y un cuestionario de 3 preguntas.

Estos son los seis trozos de código que las lecciones te piden escribir o adaptar, todos dentro de la plantilla de React Native:

- **Un formulario de dos campos** en el que pulsar un botón mueve el foco del primer `TextInput` al segundo usando una referencia.
- **Un temporizador con botones de iniciar y detener** que guarda el ID del intervalo en `useRef`, evita arrancar dos veces y limpia el intervalo al desmontar la pantalla.
- **Un componente `ProductList`** que recibe `products` y un texto de filtro, filtra con `useMemo` ignorando mayúsculas y minúsculas, pinta el resultado en un `FlatList` y luego se compara con y sin memorización.
- **Una pareja padre e hijo** donde el padre memoriza con `useCallback` la función que cambia el estado y el hijo va envuelto en `React.memo`, para que veas qué renders desaparecen.
- **Un hook `useDebouncedValue<T>(value, delay)`** y una pantalla de búsqueda que espera 350 ms desde la última tecla antes de filtrar un catálogo de cinco productos.
- **Un hook `useFetch(url)`** que devuelve `{ data, loading, error }`, consumido por una pantalla `UserProfile` que muestra un texto de carga, un mensaje de error o el nombre recibido.

![Maqueta en un iPhone de la pantalla ProductList de la lección 02.2: un título Product List, un campo de texto con el marcador Type to filter y una lista desplazable con elementos como Monitor, Mouse, Keyboard, Camera y Micron, con el rótulo Using useMemo al pie de la pantalla](https://raw.githubusercontent.com/breatheco-de/advanced-hooks-and-composition-in-react-native/main/.learn/assets/imagen-productlist.png)

## 🎓 ¿Qué necesitas antes de empezar?

- **Fundamentos de React**: componentes de función, props, `useState` y `useEffect`. Todas las lecciones dan por sabido por qué se vuelve a renderizar un componente.
- **Nociones de TypeScript**: tipar props y objetos sencillos, del estilo `type Product = { id: string; name: string }`. La lección del debounce añade un parámetro genérico.
- **Nociones de React Native**: `View`, `Text`, `Button`, `TextInput` y `FlatList` aparecen en casi todos los ejemplos.
- **Para leer las lecciones**: nada. Se abren en el navegador y no hay que instalar nada.
- **Para ejecutar el código**: un entorno de React Native CLI funcionando para la plantilla [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello). Su README pide Node 20, Java 17 (Temurin), Android Studio Jellyfish o superior con Android SDK 36 y Build-Tools 36, Xcode 16.1 o posterior para iOS, y Ruby 3.1.0 para CocoaPods. La [guía oficial de configuración del entorno](https://reactnative.dev/docs/set-up-your-environment) lo explica paso a paso.

## ✅ ¿Cómo se comprueba tu trabajo?

Aquí no hay corrección automática, y conviene saberlo antes de empezar: las 17 carpetas contienen solo `README.md` y `README.es.md`, sin ficheros de partida ni suite de tests, y en `.learn/config.json` todas las lecciones están marcadas como `"graded": false`. Nada se ejecuta contra el código que escribes. Lo que sí te da el paquete son tres formas de comprobarte a ti mismo:

- **Cuatro cuestionarios de opción múltiple**, 11 preguntas en total, repartidas entre `useRef` (3), `useMemo` (3), `useCallback` (2) y hooks propios (3). La opción correcta forma parte de la lección, así que la respuesta llega al momento.
- **Dos preguntas de respuesta abierta**, en la lección del temporizador y en la introducción a `useCallback`. Cada una viene con las respuestas modelo, marcadas como correctas o incorrectas, con las que se contrasta tu explicación.
- **La propia app**. Ejecuta tu componente en la plantilla y la comprobación es visual: el contador sigue avanzando, el foco salta al siguiente campo, el hijo deja de redibujarse.

> 💡 Para las lecciones de memorización, la comprobación más útil es meter un `console.log` dentro del componente que no debería volver a renderizarse y luego trastear con la pantalla. Si el log sigue saltando, la memorización no está haciendo lo que crees.

## 💡 ¿Qué errores debes evitar?

- **Guardar el ID del intervalo en `useState`**. Cada segundo provocaría un render por un valor que la interfaz no muestra. Ese es justo el caso para el que existe `useRef`.
- **Arrancar el temporizador dos veces**. Sin la guarda `if (intervalRef.current) return;`, una segunda pulsación crea un segundo intervalo y el contador empieza a saltar de dos en dos.
- **Olvidar la limpieza**. La lección devuelve `stopTimer()` desde `useEffect` a propósito: un intervalo que sobrevive a la pantalla sigue llamando a `setSeconds` sobre un componente que ya no existe.
- **Llamar a `ref.current.focus()` sin encadenamiento opcional**. Una referencia vale `null` hasta que el componente se monta; por eso el ejemplo escribe `passwordRef.current?.focus()`.
- **Memorizar todo por costumbre**. La lección de `useCallback` lo dice sin rodeos: memorizar también cuesta. Úsalo cuando detectes renders innecesarios, no por sistema.
- **Usar `useCallback` con un hijo sin memorizar**. Mantener estable la referencia no sirve de nada si el hijo no está envuelto en `React.memo` o la función no es una prop de `FlatList`.
- **Equivocarte con el array de dependencias**. El filtro de productos depende de `[products, filter]`; si te dejas uno, la lista se queda obsoleta sin avisar. En `useCallback`, añade una dependencia solo si la función lee de verdad un valor externo.
- **Filtrar distinguiendo mayúsculas**. El ejercicio de `ProductList` exige ignorar mayúsculas y minúsculas, así que pasa a minúsculas tanto el nombre del producto como la búsqueda.
- **Hacer debounce sin limpiar el temporizador**. `useDebouncedValue` funciona porque el efecto devuelve `clearTimeout(id)` y depende de `[value, delay]`; sin eso, el valor se actualiza igual en cada tecla.
- **Tomar el ejemplo de `useFetch` como código de producción**. No cancela peticiones ni reintenta, y por eso la lección termina pidiéndote que lo añadas.

## ❓ Preguntas frecuentes

### ¿Qué diferencia hay entre useRef y useState en React Native?

Los dos conservan un valor entre renders, pero solo `useState` programa un nuevo render cuando ese valor cambia. `useRef` te da una caja mutable en `.current` que React no vigila, así que escribir en ella no cuesta nada en pantalla. Usa estado para lo que el usuario ve y una referencia para lo que no: IDs de intervalos y timeouts, valores anteriores, contadores internos y referencias a componentes nativos como `TextInput` o `ScrollView`.

### ¿Necesito instalar algo para seguir este tutorial?

Para leer las 17 lecciones, no: son Markdown y se abren en el navegador. Para ejecutar los ejercicios sí hace falta un entorno de React Native CLI, porque este repositorio no trae código de aplicación propio. Las lecciones te remiten a la plantilla `react-native-cli-hello`, que pide Node 20, Java 17, Android Studio con el SDK 36 y, si compilas para iOS, Xcode 16.1 junto a Ruby 3.1.0.

### ¿Cuándo no conviene usar useMemo ni useCallback?

Cuando no hay un problema medible. Ambos hooks guardan un valor y comparan un array de dependencias en cada render, así que aplicarlos a un cálculo barato o a una función que va a un hijo normal sin memorizar añade trabajo sin quitar ninguno. Las lecciones los recomiendan en tres escenarios: cálculos costosos, resultados que llegan a hijos con `React.memo`, y callbacks que se pasan como props de lista, como `renderItem` o `keyExtractor`.

### ¿Este tutorial cubre compound components y patrones de composición?

Solo de forma indirecta, y conviene saberlo de antemano. La descripción del curso menciona patrones de composición como los compound components, pero ninguna de las 17 lecciones está dedicada a ellos. La composición que practicas aquí es la de los hooks: sacar la lógica compartida a `useDebouncedValue` y `useFetch`, y partir una pantalla en un padre y un hijo memorizado que recibe props estables.

### ¿Los ejercicios se corrigen automáticamente?

No. El paquete no incluye ficheros de test y todas las lecciones están declaradas como no evaluadas en su configuración. La comprobación llega por los cuatro cuestionarios, las dos preguntas abiertas y la ejecución de los componentes en la plantilla de React Native. Si buscas un paquete con corrector automático, elige uno que traiga una librería de testing incorporada.

### ¿Es gratis y puedo reutilizar el material?

Leerlo y hacerlo no cuesta nada en [4geeks.com](https://4geeks.com/es/interactive-exercise/advanced-hooks-and-composition-in-react-native--es), y el código que escribas mientras lo sigues es tuyo. Redistribuirlo es otra cosa: el repositorio no incluye fichero `LICENSE`, así que el contenido no se publica como open source y al texto de las lecciones se le aplican las reglas habituales de derechos de autor. Enlázalo en vez de republicarlo.

<!-- hide -->
## 📚 Tutoriales interactivos relacionados

- [Tutorial de React Native CLI con Zustand y TypeScript](https://4geeks.com/es/interactive-exercise/tutorial-de-react-native-cli-con-zustand-y-type-es)
- [Pruebas Unitarias con React Native Testing Library](https://4geeks.com/es/interactive-exercise/pruebas-unitarias-con-react-native-testing-libr-es)
- [Integración nativa de la cámara en React Native CLI con TypeScript](https://4geeks.com/es/interactive-exercise/integracion-nativa-de-la-camara-en-react-native-es)

## 🚀 Cómo empezar

El camino rápido no requiere ninguna instalación:

1. Abre el tutorial en [4geeks.com](https://4geeks.com/es/interactive-exercise/advanced-hooks-and-composition-in-react-native--es) y recorre las lecciones en orden, del `00.0` al `04.3`.
2. Ten abierta en otra ventana la plantilla [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello). Ahí es donde deben vivir el temporizador, el `ProductList` y los hooks propios.
3. Haz la lección de práctica antes de su cuestionario. Las preguntas dan por hecho que ya escribiste el código.

## 💻 Instalación local

Este repositorio es un conjunto de lecciones en Markdown, así que aquí no hay nada que compilar. Puedes leerlo en local con la CLI de [LearnPack](https://4geeks.com/docs/learnpack/quickstart-for-learners):

1. Instala [Node.js](https://nodejs.org) — la plantilla de código espera la versión 20, y con [nvm](https://github.com/nvm-sh/nvm) cambiar de versión es inmediato.
2. Clona este repositorio y sitúate en su raíz, la carpeta donde está `learn.json`.
3. Instala la CLI y arranca el lector de lecciones:

   ```bash
   npm i @learnpack/learnpack -g
   learnpack start
   ```

4. En otra carpeta aparte, clona la plantilla [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) y déjala funcionando antes de la primera práctica:

   ```bash
   npm install
   bundle install && bundle exec pod install   # solo para iOS
   npx react-native start --reset-cache
   ```

## 📝 Cómo están organizadas las lecciones

Cada lección vive en su propia carpeta dentro de [`exercises/`](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/tree/HEAD/exercises), nombrada con su número y su tema, por ejemplo `03.2-practice-usecallback-with-a-child-component`. Dentro hay exactamente dos ficheros, `README.md` y `README.es.md`, ambos con un pequeño bloque de frontmatter que anota el tiempo de lectura y un índice de legibilidad. No hay ficheros de partida, ni soluciones, ni tests. El orden de lectura sale de los valores `position` de `.learn/config.json`, y las imágenes compartidas están en `.learn/assets`.

## 🤝 Contribuidores

- [Rosinni Rodríguez (rosinni)](https://github.com/rosinni) — autoría del curso: las 17 lecciones en los dos idiomas 📖
- [Alejandro Sánchez (alesanchezr)](https://github.com/alesanchezr) — empaquetado de `learn.json` 💻

Se agradece cualquier aportación: si detectas un error, una errata o un fragmento desactualizado, [abre un issue](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/issues) o manda un pull request. Puedes ver a [todas las personas que han contribuido](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/graphs/contributors).

Este tutorial lo construye y mantiene [4Geeks Academy](https://4geeksacademy.com/es/coding-bootcamps/desarrollador-full-stack) junto a su comunidad.
<!-- endhide -->
