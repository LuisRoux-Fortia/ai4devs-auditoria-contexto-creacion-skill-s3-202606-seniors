---
name: list-adonisjs-routes
description: List the HTTP routes registered in the AdonisJS API. Use when the
  user wants to see the available endpoints, inspect methods/paths/middleware,
  or verify a route was wired up after an OpenSpec change.
metadata:
  author: Luis Roux
  version: "1.0"
---

List the API routes registered by the AdonisJS backend and present them clearly.

**Steps**

1. **List the routes from `backend/`:**
   ```bash
   node ace list:routes
   ```

2. **Present the result** as a table with: HTTP method, path, the controller +
   action handling it, and any middleware (notably `auth`). Group public routes
   (`/api/v1/auth/*`) separately from protected routes (`/api/v1/account/*`) to
   make the auth boundary obvious.

3. This skill is **read-only**: never edit `start/routes.ts`, controllers, or any
   source as part of listing routes.
