---
readingTime:
  minutes: 1
  words: 241
fkglResult: 18.11
---

# 02.2 Implement useMemo in a Product List

In the React Native template you have been working on, create a component called **`ProductList`** that meets the following objectives:

1. Receive a list of products (`products`) and a filter text (`filter`).
2. Use **`useMemo`** to filter the products whose name contains the filter text, **ignoring case sensitivity**.
3. Render the filtered list using **`FlatList`**.
4. Compare the component's performance **with and without `useMemo`**, observing:
   - The number of filtering calculations performed.
   - The smoothness of the interface when interacting with the list

![/.learn/assets/imagen-productlist.png](/.learn/assets/imagen-productlist.png)