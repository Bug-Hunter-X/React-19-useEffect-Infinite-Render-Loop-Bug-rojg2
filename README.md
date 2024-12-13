# React 19 useEffect Infinite Render Loop Bug

This repository demonstrates a common bug in React 19 applications involving infinite render loops caused by misusing the `useEffect` hook.  The bug occurs when an effect depends on a state variable that is updated within the effect itself, creating a cycle.

## Bug Description
The provided `bug.js` file contains a React component with an `useEffect` hook that logs a message to the console after each render. However, this effect has no dependency array, which makes it run after every render.  This isn't an error itself, but when combined with the state update this leads to an infinite loop. Each render triggers the effect which updates the state which causes another render and so on.

## Solution
The `bugSolution.js` file demonstrates how to resolve this issue by using the dependency array. This array explicitly states which values the effect depends on, and if it's empty, `[]`,  it means it runs only once after the initial render, preventing infinite loops.

## How to Reproduce
1. Clone the repository.
2. Navigate to the directory containing `bug.js` and run using a React development server (e.g. `npm start`).
3. Observe the error that may lead to a crash or very high CPU usage. (Note: The browser may crash before you see the error).
4. Repeat step 2 and 3 by using `bugSolution.js` to see the solution.
