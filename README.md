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
- connecting a repository to a hosting platform
- building a foundation for a CI/CD pipeline

The project is intentionally kept simple so that each stage of the process is easy to understand, without unnecessary backend or infrastructure complexity.

---

## Tech Stack

- React
- Vite
- JavaScript
- Git
- GitHub
- Cloudflare Pages

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

### 3. Cloudflare Pages was configured

The project was connected to **Cloudflare Pages** using the **GitHub integration** flow.

The deployment was configured through the following steps:

#### 3.1. Opened the Cloudflare dashboard

<img width="1498" height="869" alt="Screenshot 2026-03-26 at 18 06 55" src="https://github.com/user-attachments/assets/0c522a2d-12f8-4c5a-aa85-afd4dbd04f43" />

The Cloudflare dashboard was opened and the Pages flow was selected instead of the Worker flow.

This was important because the project is currently a simple frontend application built with React + Vite, so **Cloudflare Pages** is the correct deployment target.

#### 3.2. Chose the Pages deployment flow

<img width="1073" height="546" alt="Screenshot 2026-03-26 at 18 18 39" src="https://github.com/user-attachments/assets/193c73c5-c80c-457f-b846-8fbcf874c0d9" />

From the available options, the **Pages** setup was used instead of creating a Worker.

Then the option below was selected:

- **Import an existing Git repository**


This was the correct choice because the project was already pushed to GitHub and was ready to be connected directly to a hosting platform.

#### 3.3. Selected the GitHub repository

<img width="1028" height="776" alt="Screenshot 2026-03-26 at 18 19 14" src="https://github.com/user-attachments/assets/a61fb1c1-2b99-4aa5-a185-83c1fa255a35" />

The repository below was selected from GitHub:

- `ninkov/DevOpsTraining`

This step connected the project source code to Cloudflare Pages.

#### 3.4. Configured the deployment settings

<img width="1038" height="783" alt="Screenshot 2026-03-26 at 18 24 46" src="https://github.com/user-attachments/assets/c00e5f35-82d8-479f-8e9a-54d94c4ef7dd" />


The following deployment settings were used:

- **Project name:** `devopstraining`
- **Production branch:** `main`
- **Build command:** `npm run build`
- **Build output directory:** `dist`

These settings tell Cloudflare:
- which branch should be treated as production
- how the project should be built
- which folder should be published after the build is completed

#### 3.5. Saved the configuration and deployed the project

<img width="1019" height="766" alt="Screenshot 2026-03-26 at 18 27 50" src="https://github.com/user-attachments/assets/a958916f-0501-44b9-9035-cafebd9c9b83" />

After saving the settings, Cloudflare automatically:

1. pulled the source code from GitHub
2. installed the project dependencies
3. ran the build command
4. published the generated output

The project was successfully deployed and published at:

<img width="807" height="383" alt="Screenshot 2026-03-26 at 18 37 42" src="https://github.com/user-attachments/assets/4f95ea0e-6a96-4549-b79b-562634d5e1f3" />

```text
https://devopstraining.pages.dev
