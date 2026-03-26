# DevOps Training App

A minimal React + Vite application created for training purposes to practice a basic DevOps workflow:

- local development
- Git version control
- connecting a project to a GitHub repository
- preparing for deployment
- preparing a CI/CD pipeline
- next step: deployment with Cloudflare Pages

---

## Project Purpose

This project was created as a simplified starter frontend application to help learn the process of:

- creating an application
- working with Git
- pushing code to GitHub
- running a local build
- preparing for automated deployment
- building a foundation for a CI/CD pipeline

The project is intentionally kept simple so that each stage of the process is easy to understand, without unnecessary backend or infrastructure complexity.

---

## Tech Stack

- React
- Vite
- JavaScript
- Git
- GitHub

---

## Progress So Far

### 1. A new React + Vite project was created

The project was initialized as a minimal frontend application.

### 2. `App.jsx` was simplified

The application currently contains only a basic heading, making it easier to work with a minimal codebase and follow the deployment flow more clearly.

Example:

```jsx
import './App.css'

function App() {
  return (
    <>
      <h1>React + Vite Training</h1>
    </>
  )
}

export default App
```