# React Native useRef Hook Not Updating Value Inside useCallback

This repository demonstrates a common issue with the `useRef` hook in React Native when used within `useCallback`.  The ref may not update as expected due to the timing of updates within a frequently rendering component. This example shows the problem and provides a solution.

## Problem

The `useRef` hook is intended to persist values between renders. However, when combined with `useCallback`, the callback function's closure might capture an outdated value of the ref. This means that when the component re-renders and the ref's value changes, the callback function may still use the old value.

## Solution

The solution is to ensure that the callback function is recreated every time the ref value changes. We can achieve this by including the ref's current value in the dependency array of `useCallback`.