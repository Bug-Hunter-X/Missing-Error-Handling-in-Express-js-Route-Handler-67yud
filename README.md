# Express.js Route Handler Error Handling Bug

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  The `bug.js` file shows the buggy code, which fails to handle cases where the user ID is not a valid integer.  The `bugSolution.js` file provides the corrected code with proper error handling.

## Bug Description

The `/users/:id` route attempts to find a user based on the ID passed in the URL.  However, if the ID is not a valid integer, the `parseInt(userId)` call will return `NaN`, causing the `users.find` method to fail silently or potentially throw an error.  This leads to unpredictable behavior and makes the application vulnerable to crashes or unexpected responses.

## Solution

The solution involves adding explicit error handling to check if the parsed user ID is a valid number. If not, it returns a 400 Bad Request response instead of proceeding with the potentially failing user lookup.