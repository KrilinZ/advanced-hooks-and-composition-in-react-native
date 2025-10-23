---
readingTime:
  minutes: 1
  words: 241
fkglResult: 18.11
---

# 02.2 Implementa useMemo en una Lista de Productos



En la plantilla React Native que vienes trabjando, crea un componente llamado **`ProductList`** que cumpla con los siguientes objetivos:

1. Reciba una lista de productos (`products`) y un texto de filtro (`filter`).
2. Utilice **`useMemo`** para filtrar los productos cuyo nombre contenga el texto del filtro, **ignorando mayúsculas y minúsculas**.
3. Renderice la lista filtrada mediante **`FlatList`**.
4. Compare el rendimiento del componente **con y sin `useMemo`**, observando:
   - La cantidad de cálculos de filtrado realizados.
   - La fluidez de la interfaz al interactuar con la lista

![/.learn/assets/imagen-productlist.png](/.learn/assets/imagen-productlist.png)









