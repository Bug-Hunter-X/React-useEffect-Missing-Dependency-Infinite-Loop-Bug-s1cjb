# React useEffect Missing Dependency Bug

This repository demonstrates a common bug in React's `useEffect` hook: forgetting to include necessary dependencies in the dependency array. This can lead to unexpected behavior, such as infinite loops or incorrect updates.

## Bug Description
The `MyComponent` component uses `useEffect` to update a counter every second. However, the dependency array is empty (`[]`), meaning the effect runs only once after the component mounts.  This is incorrect. The effect depends on `count`, which is mutated every second.  The `setInterval` call is never stopped.  This causes an infinite loop even after the component is unmounted.

## Bug Solution
The solution involves adding `count` to the dependency array.  This ensures the effect runs only when the `count` value changes.  The `clearInterval` function called in the cleanup function is still necessary to stop the `setInterval` when the component unmounts.