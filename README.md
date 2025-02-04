# Express.js Route Handler Missing Error Handling for Invalid User IDs

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input. Specifically, the route `/users/:id` attempts to parse the `id` parameter as an integer without checking if it's actually a number. This can lead to unexpected behavior or crashes if the `id` is not a valid integer.

## Bug

The `bug.js` file contains the buggy code. The issue lies in the line `const user = users.find(user => user.id === parseInt(userId));`. If `userId` is not a number (e.g., a string or null), `parseInt(userId)` will return `NaN`, leading to `user` always being `null` and the code silently failing or producing unexpected results.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  This version includes explicit error handling to check if `userId` is a valid number before attempting to parse it.  If it's not a number, an appropriate error response is sent.

## How to Run

1. Clone this repository.
2. Run `npm install` to install Express.js.
3. Run `node bug.js` to see the original buggy code in action (requires a `users` array to be defined in the scope).
4. Run `node bugSolution.js` to see the corrected code in action.