# Closure issue in setTimeout loop
This example demonstrates a common issue with closures in JavaScript's `setTimeout` function within a loop.  The expected output is the numbers 0 through 9, each printed after a 1-second delay. However, due to the way closures work in JavaScript, the output will be 10 ten times.

## Bug Description
The problem stems from the fact that the `setTimeout` callbacks do not capture the value of `i` at the time they are created; instead, they capture a reference to the variable `i`. By the time the `setTimeout` callbacks finally execute, the loop has already completed, and `i` holds its final value of 10.

## Solution
To fix this, we need to ensure that each `setTimeout` callback gets its own copy of the loop variable.  This can be achieved using an Immediately Invoked Function Expression (IIFE) or `let` within the loop, which will create a new scope for each iteration.