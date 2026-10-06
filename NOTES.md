## Summary of Changes

I identified and fixed five high-value issues across the backend, SQL, and frontend:

1. Fixed SQL operator precedence in the task search query so the status filter applies correctly to title and description searches. Updated the H2 and Oracle reference SQL to remain consistent with the backend.
2. Removed artificial `Thread.sleep()` latency from the task search API.
3. Added validation for invalid `page` and `pageSize` values so the API returns HTTP 400 instead of a server error.
4. Reset pagination to page 1 whenever the search query or status filter changes.
5. Prevented stale API responses from overwriting newer search results and fixed loading/error state handling in the task hook.

## What I Chose Not to Change

I kept the existing application structure, API design, database schema, and pagination approach unchanged to keep the patch focused. I also left the Spring `open-in-view` warning unchanged because it was not directly related to the task-tracking functionality.

I did not perform broader refactoring or add new dependencies because the exercise prioritizes focused, high-value fixes.

## Biggest Remaining Risk

The backend currently loads all matching tasks and performs pagination in memory. This may become inefficient as the dataset grows. Database-level pagination would be a better long-term improvement.

## Tools / AI Used

I used ChatGPT to review code, reason about SQL precedence, identify edge cases, and discuss focused fixes. I used VS Code, PowerShell, browser-based UI testing, and direct API requests to reproduce and verify the issues. I reviewed and tested the suggested changes before applying them.