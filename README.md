# React 18/19 useEffect Stale Closure Bug

This repository demonstrates a subtle bug related to stale closures in `useEffect` hooks with empty dependency arrays in React 18 and 19.  The issue arises when an effect accesses a state variable, expecting it to reflect updates, but instead receives the initial value because of the timing of closures.

## Problem
The `useEffect` hook with `[]` as dependency array is intended to run only once after the initial render. However, if it captures state variables, the values captured are not live; they are the initial values present at the time the component renders for the first time.  Any subsequent state changes will not be reflected in that specific `useEffect` call.

## Solution
The solution is to either pass the relevant state variable as a dependency to the `useEffect` hook or, if you need to run the effect only once, to ensure the state variable you're using is appropriately managed so the effect uses the correct value.

## How to Run
1. Clone this repository.
2. Navigate to the project directory.
3. Run `npm install`.
4. Run `npm start`.
