<!-- hide -->
<div align="center">

# Advanced Hooks and Composition in React Native with TypeScript

[![Certified by 4Geeks](https://img.shields.io/badge/4Geeks-certified-2563eb)](https://4geeks.com/en/interactive-exercise/advanced-hooks-and-composition-in-react-native--en)
[![Built with LearnPack](https://img.shields.io/badge/LearnPack-tutorial-2563eb)](https://4geeks.com/docs/learnpack)
[![Template react-native-cli-hello](https://img.shields.io/badge/Template-react--native--cli--hello-fb5a1f)](https://github.com/breatheco-de/react-native-cli-hello)

</div>
<!-- endhide -->

This interactive tutorial teaches advanced React Native hooks with TypeScript across 17 short lessons, estimated at 60 minutes. You practise `useRef` for native component references and interval IDs, `useMemo` to filter a product list, `useCallback` to keep a `FlatList` `renderItem` stable, and custom hooks such as `useDebouncedValue` and `useFetch`. It ships 6 hands-on challenges plus 4 quizzes with 11 questions, and the code you write runs inside the separate `react-native-cli-hello` template.

<!-- hide -->
## 📋 About this tutorial

- **Difficulty**: Beginner (`"difficulty": "beginner"` in `learn.json`)
- **Estimated duration**: 60 minutes. The 17 lesson files declare about 18 minutes of reading and roughly 3,800 words
- **Lessons**: 17 folders inside `exercises/`, numbered `00.0` to `04.3`
- **Practice**: 6 build-it-yourself challenges, 4 multiple-choice quizzes (11 questions) and 2 open-answer questions
- **Technologies**: React Native, TypeScript, mobile development
- **Where the code runs**: the [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) template, a separate repository
- **Grading**: none automated — this package contains no test files
- **Languages**: [English](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/blob/HEAD/README.md) · [Español](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/blob/HEAD/README.es.md)
<!-- endhide -->

## 🎯 What will you learn?

- How [`useRef`](https://react.dev/reference/react/useRef) stores a mutable value that survives re-renders **without triggering one**, and why that makes it the right place for an interval ID.
- How to point a ref at a native component and call its methods, for example jumping the keyboard focus to the next `TextInput` with `passwordRef.current?.focus()`.
- How [`useMemo`](https://react.dev/reference/react/useMemo) caches the result of an expensive calculation and recomputes it only when its dependency array changes, keeping a filtered [`FlatList`](https://reactnative.dev/docs/flatlist) smooth while the user types.
- How [`useCallback`](https://react.dev/reference/react/useCallback) keeps a function reference stable between renders, so children wrapped in [`React.memo`](https://react.dev/reference/react/memo) and list props like `renderItem` and `keyExtractor` stop re-rendering for no reason.
- Why memoization is not free, and the signal that tells you to reach for it: you are seeing renders that change nothing on screen.
- How to extract repeated logic into a custom hook, typed with TypeScript [generics](https://www.typescriptlang.org/docs/handbook/2/generics.html) so `useDebouncedValue<T>(value, delay)` returns the same type it receives.
- How a data-fetching hook returns `{ data, loading, error }` and lets several screens share one request lifecycle instead of copying `fetch` calls around.

![Diagram from lesson 04.0: three boxes labelled Component A, Component B and Component C all point to a single blue useFetch box, which in turn branches into loading, data and error states and to an API Call box, under the caption Reuse](https://raw.githubusercontent.com/breatheco-de/advanced-hooks-and-composition-in-react-native/main/.learn/assets/image-usefetch.png)

## 👀 What will you build?

The 17 lessons are grouped in five blocks. Every lesson is a Markdown file: eight of them carry a TypeScript or JavaScript snippet, four are quizzes, and the rest are theory or the brief for code you write yourself:

- **`00.0` Welcome (1 lesson)** — a one-minute intro that names what is coming: `useRef`, `useMemo`, `useCallback` and reusing logic across components.
- **`01.0` to `01.4` — useRef (5 lessons)** — the difference between a ref and state, refs pointing at native components, refs holding mutable values, a start/stop timer whose `setInterval` ID lives in a ref, and a 3-question quiz.
- **`02.0`, `02.2`, `02.3` — useMemo (3 lessons)** — when a recalculation is worth caching, a `ProductList` component you write yourself, and a 3-question quiz. The folder numbering jumps straight from `02.0` to `02.2`; there is no `02.1`.
- **`03.0` to `03.3` — useCallback (4 lessons)** — what function identity has to do with re-renders, stable `renderItem` and `keyExtractor` for a `FlatList`, a parent/child exercise with `React.memo`, and a 2-question quiz.
- **`04.0` to `04.3` — Custom hooks (4 lessons)** — when to extract a hook, a `useDebouncedValue` hook built from scratch, a `useFetch` walkthrough with a sequence diagram of the request lifecycle, and a 3-question quiz.

These are the six pieces of code the lessons ask you to write or adapt, all of them inside the React Native template:

- **A two-field login form** where pressing a button moves focus from the first `TextInput` to the second through a ref.
- **A timer with Start and Stop buttons** that keeps the interval ID in `useRef`, guards against starting twice and clears the interval when the screen unmounts.
- **A `ProductList` component** that receives `products` and a `filter` string, filters with `useMemo` ignoring upper and lower case, renders the result in a `FlatList`, and is then compared with and without memoization.
- **A parent/child pair** where the parent memoizes its state-updating function with `useCallback` and the child is wrapped in `React.memo`, so you can watch which renders disappear.
- **A `useDebouncedValue<T>(value, delay)` hook** plus a search screen that waits 350 ms after the last keystroke before filtering a five-product catalogue.
- **A `useFetch(url)` hook** returning `{ data, loading, error }`, consumed by a `UserProfile` screen that shows a loading text, an error message or the fetched name.

![iPhone mockup of the ProductList screen from lesson 02.2: a Product List heading, a text input with the placeholder Type to filter, and a scrollable list of items including Monitor, Mouse, Keyboard, Camera and Micron, with the caption Using useMemo at the bottom of the screen](https://raw.githubusercontent.com/breatheco-de/advanced-hooks-and-composition-in-react-native/main/.learn/assets/imagen-productlist.png)

## 🎓 What do you need before starting?

- **React fundamentals**: function components, props, `useState` and `useEffect`. Every lesson assumes you already know why a component re-renders.
- **TypeScript basics**: typing props and simple objects, such as `type Product = { id: string; name: string }`. The debounce lesson also uses a generic parameter.
- **React Native basics**: `View`, `Text`, `Button`, `TextInput` and `FlatList` appear in almost every snippet.
- **To read the lessons**: nothing. They open in the browser and no installation is involved.
- **To run the code**: a working React Native CLI environment for the [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) template. Its README asks for Node 20, Java 17 (Temurin), Android Studio Jellyfish or newer with Android SDK 36 and Build-Tools 36, Xcode 16.1 or later for iOS, and Ruby 3.1.0 for CocoaPods. The [official environment setup guide](https://reactnative.dev/docs/set-up-your-environment) walks through it.

## ✅ How is your work checked?

There is no automated grading here, and it is worth knowing before you start: the 17 folders contain only `README.md` and `README.es.md`, with no starter files and no test suite, and every entry in `.learn/config.json` is marked `"graded": false`. Nothing runs against the code you write. What the package does give you is three ways to check yourself:

- **Four multiple-choice quizzes**, 11 questions in total, covering `useRef` (3), `useMemo` (3), `useCallback` (2) and custom hooks (3). The correct option is part of the lesson, so you get immediate feedback.
- **Two open-answer questions**, in the timer lesson and in the `useCallback` intro. Each one ships with the model answers, marked as correct or incorrect, that your written explanation is measured against.
- **The app itself**. Run your component in the template and the feedback is visual: the counter keeps ticking, the focus jumps to the next field, the child stops re-rendering.

> 💡 The most useful check for the memoization lessons is to add a `console.log` inside the component that should not re-render, then interact with the screen. If the log keeps firing, the memoization is not doing what you think.

## 💡 What mistakes should you avoid?

- **Keeping the interval ID in `useState`**. Every tick would re-render the component for a value the interface never shows. That is exactly the case `useRef` exists for.
- **Starting the timer twice**. Without the `if (intervalRef.current) return;` guard, a second press of Start creates a second interval and the counter jumps two seconds at a time.
- **Skipping the cleanup**. The lesson returns `stopTimer()` from `useEffect` on purpose: an interval that outlives the screen keeps calling `setSeconds` on a component that no longer exists.
- **Calling `ref.current.focus()` without optional chaining**. A ref is `null` until the component mounts, which is why the example writes `passwordRef.current?.focus()`.
- **Memoizing everything by default**. The `useCallback` lesson is explicit: memoizing has a cost of its own. Reach for it when you can see unnecessary renders, not as a habit.
- **Using `useCallback` while the child is not memoized**. A stable function reference changes nothing unless the child is wrapped in `React.memo` or the function is a `FlatList` prop.
- **Getting the dependency array wrong**. The product filter depends on `[products, filter]`; drop one and the list silently goes stale. In `useCallback`, add a dependency only when the function actually reads an external value.
- **Filtering case-sensitively**. The `ProductList` exercise requires the filter to ignore case, so lowercase both the product name and the query before comparing.
- **Debouncing without clearing the timeout**. `useDebouncedValue` only works because the effect returns `clearTimeout(id)` and depends on `[value, delay]`; without that the value updates once per keystroke anyway.
- **Treating the `useFetch` example as production-ready**. It has no request cancellation and no retries, which is why the lesson ends by asking you to add them.

## ❓ Frequently asked questions

### What is the difference between useRef and useState in React Native?

Both keep a value between renders, but only `useState` schedules a re-render when the value changes. `useRef` gives you a mutable `.current` box that React never watches, so writing to it costs nothing on screen. Use state for anything the user sees, and a ref for things they do not: interval and timeout IDs, previous values, counters used internally, and references to native components such as `TextInput` or `ScrollView`.

### Do I need to install anything to follow this tutorial?

To read the 17 lessons, no: they are Markdown and open in the browser. To run the exercises you need a React Native CLI environment, because this repository has no application code of its own. The lessons point you at the `react-native-cli-hello` template, which expects Node 20, Java 17, Android Studio with SDK 36, and Xcode 16.1 plus Ruby 3.1.0 if you are building for iOS.

### When should I not use useMemo or useCallback?

When there is no measurable problem. Both hooks store a value and compare a dependency array on every render, so applying them to a cheap calculation or to a function that is passed to a plain, non-memoized child adds work without removing any. The lessons recommend them in three situations: expensive calculations, results passed to `React.memo` children, and callbacks handed to list props such as `renderItem` and `keyExtractor`.

### Does this tutorial cover compound components and composition patterns?

Only indirectly, and it is fair to know in advance. The course description mentions composition patterns such as compound components, but none of the 17 lessons is dedicated to them. The composition you practise here is the hook-based kind: pulling shared logic out into `useDebouncedValue` and `useFetch`, and splitting a screen into a parent and a memoized child that receives stable props.

### Are the exercises graded automatically?

No. The package ships no test files, and every lesson is declared as not graded in its configuration. You confirm your answers with the four quizzes, the two open-answer questions, and by running the components in the React Native template. If you want a package with a test runner attached, look for one of the tutorials that includes a testing library.

### Is this tutorial free, and can I reuse the material?

Reading and running it costs nothing on [4geeks.com](https://4geeks.com/en/interactive-exercise/advanced-hooks-and-composition-in-react-native--en), and the code you write while following it is yours. Redistribution is a separate question: the repository ships no `LICENSE` file, so the content is not released as open source and the usual copyright defaults apply to the lesson text. Link to it rather than republishing it.

<!-- hide -->
## 📚 Related interactive tutorials

- [React Native CLI Tutorial with Zustand and TypeScript](https://4geeks.com/en/interactive-exercise/react-native-cli-tutorial-with-zustand-and-type-en)
- [Unit Testing with React Native Testing Library](https://4geeks.com/en/interactive-exercise/unit-testing-with-react-native-testing-library-en)
- [Native Camera Integration in React Native CLI with TypeScript](https://4geeks.com/en/interactive-exercise/native-camera-integration-in-react-native-cli-w-en)

## 🚀 How to start

The quickest path needs no setup at all:

1. Open the tutorial on [4geeks.com](https://4geeks.com/en/interactive-exercise/advanced-hooks-and-composition-in-react-native--en) and work through the lessons in order, from `00.0` to `04.3`.
2. Keep the [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) template open in a second window. That is where the timer, the `ProductList` and the custom hooks are meant to live.
3. Do the practice lesson before its quiz. The quiz questions assume you already wrote the code.

## 💻 Local installation

This repository is a set of Markdown lessons, so there is nothing to compile here. You can read it locally with the [LearnPack](https://4geeks.com/docs/learnpack/quickstart-for-learners) CLI:

1. Install [Node.js](https://nodejs.org) — version 20 is what the code template expects, and [nvm](https://github.com/nvm-sh/nvm) makes switching easy.
2. Clone this repository and open its root, the folder that contains `learn.json`.
3. Install the CLI and start the lesson browser:

   ```bash
   npm i @learnpack/learnpack -g
   learnpack start
   ```

4. In a separate folder, clone the [`react-native-cli-hello`](https://github.com/breatheco-de/react-native-cli-hello) template and get it running before the first practice lesson:

   ```bash
   npm install
   bundle install && bundle exec pod install   # iOS only
   npx react-native start --reset-cache
   ```

## 📝 How the exercises are organized

Every lesson lives in its own folder inside [`exercises/`](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/tree/HEAD/exercises), named with its number and topic, for example `03.2-practice-usecallback-with-a-child-component`. Each folder holds exactly two files, `README.md` and `README.es.md`, both opening with a small frontmatter block that records reading time and readability score. There are no starter files, no solutions and no tests. The reading order comes from the `position` values in `.learn/config.json`, and shared images live in `.learn/assets`.

## 🤝 Contributors

- [Rosinni Rodríguez (rosinni)](https://github.com/rosinni) — author of the course: the 17 lessons in both languages 📖
- [Alejandro Sánchez (alesanchezr)](https://github.com/alesanchezr) — packaging of `learn.json` 💻

Contributions of any kind are welcome: if you spot a bug, a typo or an outdated snippet, [open an issue](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/issues) or send a pull request. See [everyone who has contributed](https://github.com/breatheco-de/advanced-hooks-and-composition-in-react-native/graphs/contributors).

This tutorial is built and maintained by [4Geeks Academy](https://4geeksacademy.com/us/coding-bootcamps/part-time-full-stack-developer) and its community.
<!-- endhide -->
