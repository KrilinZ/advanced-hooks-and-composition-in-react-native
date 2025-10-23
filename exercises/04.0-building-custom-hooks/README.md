---
readingTime:
  minutes: 1
  words: 225
fkglResult: 16.75
---

# 04.0 Introduction to Custom Hooks

Custom **hooks** are functions that allow you to encapsulate and reuse logic involving React hooks, keeping your components clean and focused on the interface.

### When to create a custom hook?

- When you detect **repetition of logic** in several components.
- To manage related states and effects that can be shared.

### Practical example

Imagine you need to make API calls in different parts of your app. Instead of repeating the code, you create a `useFetch` hook that handles the request, loading state, and errors, facilitating reuse and improving readability.

---

![/.learn/assets/image-usefetch.png](/.learn/assets/image-usefetch.png)