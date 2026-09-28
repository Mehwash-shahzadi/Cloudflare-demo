# Cloudflare Demo — Todo List

A minimal Todo List app built with React, TypeScript, and Vite. No
backend, no database, no authentication — just local component state.
It exists as a simple demo for deploying a static site to Cloudflare
Pages.

## Features

- Add a todo
- Mark a todo as complete (checkbox, strikethrough)
- Delete a todo

## 1. Install dependencies

```bash
npm install
```

This reads `package.json` and downloads React, Vite, and TypeScript
into `node_modules/`.

## 2. Run locally

```bash
npm run dev
```

Starts Vite's dev server (usually at `http://localhost:5173`) with hot
module reload — edits to `src/App.tsx` show up in the browser
immediately without a full page reload.

## 3. How `npm run build` works

```bash
npm run build
```

This runs two steps:

1. `tsc -b` — type-checks the project with TypeScript, catching type
   errors before they reach production.
2. `vite build` — bundles and minifies the app (JS, CSS, HTML) into a
   small set of static files optimized for production, written to the
   `dist/` folder.

## 4. What is `dist/` and why does Cloudflare use it?

`dist/` is the build output: plain HTML, CSS, and JS files with no
build tooling or source code required to run them. Because it's fully
static, it can be served directly from a CDN with no server-side
runtime.

Cloudflare Pages works by taking a folder of static files and serving
them from Cloudflare's edge network. You point it at `dist/` (the
"build output directory") and it hosts exactly what's inside — no
Node.js server needed at runtime.

## 5. Deploying to Cloudflare Pages (Free Tier) via GitHub

1. **Push this project to GitHub.**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

2. **Sign in to Cloudflare** at [dash.cloudflare.com](https://dash.cloudflare.com)
   (the Free Tier is enough for this project).

3. Go to **Workers & Pages** → **Create application** → **Pages** →
   **Connect to Git**.

4. **Authorize GitHub** and select the repository you just pushed.

5. Configure the build settings:
   - **Framework preset:** Vite
   - **Build command:** `npm run build`
   - **Build output directory:** `dist`

6. Click **Save and Deploy**. Cloudflare will install dependencies, run
   the build, and publish the contents of `dist/` to a
   `*.pages.dev` URL.

7. **Done.** Every future push to the connected branch triggers an
   automatic rebuild and redeploy.
