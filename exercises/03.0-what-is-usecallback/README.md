---
readingTime:
  minutes: 1
  words: 216
fkglResult: 13.25
---

# 03.0 What is useCallback?

The goal of this lesson is to understand what **useCallback** is and when it is useful in React Native.

**useCallback** is a hook that memorizes functions to avoid recreating them on every component render. This is especially important when passing functions as props to child components optimized with **React.memo**. Without **useCallback**, each render of the parent component generates a new function, which can cause unnecessary re-renders in the children.

### When to use useCallback?

- When passing functions to child components memoized with **React.memo**.
- To avoid recreating functions on renders that do not affect the UI logic.

### Reflect and answer:

What is the main advantage of using **useCallback** in a React component? Explain in your own words.

```question eval="The user must explain that useCallback helps avoid unnecessary recreation of functions on each render, improving performance and preventing unnecessary re-renders in memoized child components."
CORRECT: useCallback prevents new functions from being created on each render, which improves performance.
CORRECT: It allows memoized child components not to re-render unnecessarily.
INCORRECT: useCallback creates new functions on each render to update the UI.
INCORRECT: useCallback is used to manage state in React.
CORRECT: It memorizes functions to keep the same reference between renders.
```