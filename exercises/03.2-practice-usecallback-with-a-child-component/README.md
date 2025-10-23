---
readingTime:
  minutes: 1
  words: 236
fkglResult: 13.42
---

# 03.2 Practice: Optimization with useCallback

When you pass functions as props to memoized child components, each render creates a new function, which can cause the child to re-render unnecessarily. **useCallback** memorizes the function and keeps its reference stable as long as its dependencies do not change.

### Practical activity:

1. Create a parent component with a state and a function that modifies that state.
2. Use **useCallback** to memorize that function.
3. Pass the memorized function as a prop to a child component memoized with **React.memo**.
4. Observe that the child component only re-renders when necessary.

![GENERATING: Diagram showing a parent component passing a memorized function with useCallback to a child component memoized with React.memo, with arrows indicating the flow of props and annotations highlighting the stability of the function reference and prevention of unnecessary re-renders](/.learn/assets/a5n4en2vmbf)