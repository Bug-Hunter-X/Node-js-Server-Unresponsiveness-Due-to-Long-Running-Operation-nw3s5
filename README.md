# Node.js Server Unresponsiveness

This repository demonstrates a common issue in Node.js where a long-running operation in a request handler can cause the server to hang or become unresponsive.  The problem stems from Node.js's single-threaded event loop.  Blocking the event loop prevents other requests from being processed.

The `server.js` file contains the buggy code. The `serverSolution.js` provides a solution using asynchronous operations.

## How to reproduce the bug

1. Clone the repository.
2. Run `node server.js`.
3. Make a request to `http://localhost:3000/`. You'll observe that subsequent requests will not be processed until the initial request completes after a 5-second delay. 

## Solution

The `serverSolution.js` demonstrates how to avoid blocking the event loop by using asynchronous techniques (e.g., `setTimeout` or promises) to handle long-running tasks.  This allows the server to remain responsive to other requests even while processing long-running operations.