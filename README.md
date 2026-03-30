# DevOps Training App

A minimal React + Vite application created for training purposes to practice a basic DevOps workflow:

- local development
- Git version control
- connecting a project to a GitHub repository
- preparing for deployment
- deployment with Cloudflare Pages
- building a foundation for a CI/CD pipeline
- adding basic CI with GitHub Actions

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
- GitHub Actions

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

### 3. Local development and build were verified

The project was checked locally to confirm that both development mode and production build were working correctly.

Commands used:

```bash
npm run dev
npm run build
```

This step was important because it confirmed that:

- the application runs locally
- the build process works correctly
- the project is ready for deployment

### 4. The project was connected to GitHub

The local project was connected to a GitHub repository so the code could be versioned, pushed remotely, and prepared for deployment automation.

Typical commands used:

```bash
git init
git branch -M main
git add .
git commit -m "init: create Vite React starter app"
git remote add origin <repository-url>
git push -u origin main
```

### 5. Cloudflare Pages was configured

The project was connected to **Cloudflare Pages** using the **GitHub integration** flow.

The deployment was configured through the following steps:

#### 5.1. Opened the Cloudflare dashboard

<img width="1498" height="869" alt="Screenshot 2026-03-26 at 18 06 55" src="https://github.com/user-attachments/assets/0c522a2d-12f8-4c5a-aa85-afd4dbd04f43" />

The Cloudflare dashboard was opened and the Pages flow was selected instead of the Worker flow.

This was important because the project is currently a simple frontend application built with React + Vite, so **Cloudflare Pages** is the correct deployment target.

#### 5.2. Chose the Pages deployment flow

<img width="1073" height="546" alt="Screenshot 2026-03-26 at 18 18 39" src="https://github.com/user-attachments/assets/193c73c5-c80c-457f-b846-8fbcf874c0d9" />

From the available options, the **Pages** setup was used instead of creating a Worker.

Then the following option was selected:

- **Import an existing Git repository**

This was the correct choice because the project was already pushed to GitHub and was ready to be connected directly to a hosting platform.

#### 5.3. Selected the GitHub repository

<img width="1028" height="776" alt="Screenshot 2026-03-26 at 18 19 14" src="https://github.com/user-attachments/assets/a61fb1c1-2b99-4aa5-a185-83c1fa255a35" />

The following repository was selected from GitHub:

- `ninkov/DevOpsTraining`

This step connected the project source code to Cloudflare Pages.

#### 5.4. Configured the deployment settings

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

#### 5.5. Saved the configuration and deployed the project

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
```

#### 5.6. Why this is important from a DevOps perspective

This step introduced a very simple form of **Continuous Deployment (CD)**.

Why this is considered CD:

- the code is stored in GitHub
- the `main` branch is connected to Cloudflare Pages
- Cloudflare automatically builds the project
- Cloudflare automatically deploys the latest version to a live public URL

This is still a basic version of CD, but it already demonstrates the core idea of automated deployment:

a code change pushed to the repository can trigger a new build and a new deployment without manually uploading files.

### 6. GitHub Actions CI workflow was added

A new GitHub Actions workflow file was created at:

```text
.github/workflows/ci.yml
```

The purpose of this workflow is to introduce a basic **Continuous Integration (CI)** process for the project.

#### 6.1. Workflow configuration

The workflow was configured to run automatically on:

- pushes to `main`
- pull requests targeting `main`

Workflow content:

```yaml
name: CI

on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

jobs:
  build-and-check:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 22
          cache: npm

      - name: Install dependencies
        run: npm ci

      - name: Run lint
        run: npm run lint --if-present

      - name: Build project
        run: npm run build
```

This workflow performs the following automated checks:

- checks out the repository
- sets up a Node.js environment
- installs dependencies with `npm ci`
- runs lint if available
- runs the production build

This step is important because it adds an automated validation layer before changes become part of the `main` branch.

#### 6.2. A feature branch was created for the CI change

Instead of changing `main` directly, a separate branch was created for the CI workflow:

```bash
git checkout -b feature/add-ci
```

The new workflow file was staged, committed, and pushed to GitHub:

```bash
git add .github/workflows/ci.yml
git commit -m "ci: add GitHub Actions build workflow"
git push -u origin feature/add-ci
```

This step is important because it introduces a safer Git workflow:

- changes are developed in isolation
- `main` is kept clean
- the new work can be reviewed through a Pull Request

#### 6.3. A Pull Request was created and validated

A Pull Request was opened from:

- **base:** `main`
- **compare:** `feature/add-ci`

The CI workflow ran automatically after the Pull Request was created.

The checks passed successfully, which confirmed that:

- the workflow file was valid
- dependencies could be installed correctly
- the project could be built successfully
- the CI process was working as expected

This was the first real CI validation for the project inside GitHub.

#### 6.4. The Pull Request was merged into `main`

After all checks passed, the Pull Request was merged into the `main` branch.

This step officially added the CI workflow to the main version of the project.

After the merge:

- the Pull Request was closed
- the feature branch was no longer needed
- the branch could be deleted safely

#### 6.5. Cloudflare Pages triggered a new production deployment

Because `main` is connected to Cloudflare Pages as the production branch, the merge triggered a new production deployment automatically.

This confirmed that the project now has both:

- a basic **CI** process through GitHub Actions
- a basic **CD** process through Cloudflare Pages

At this stage, the workflow looks like this:

```text
feature branch → pull request → CI checks → merge to main → Cloudflare production deploy
```

This is still a simple pipeline, but it already demonstrates a real DevOps workflow with both validation and deployment automation.

---

## Current Status

- [x] React + Vite app created
- [x] App component simplified
- [x] Local development verified
- [x] Production build verified
- [x] GitHub repository created and connected
- [x] Project pushed to GitHub
- [x] Cloudflare Pages connected
- [x] First live deployment completed
- [x] GitHub Actions CI workflow added
- [x] Pull Request created for CI change
- [x] CI checks passed successfully
- [x] CI workflow merged into `main`
- [x] Cloudflare production redeployment confirmed

---

## Current DevOps Flow

```text
code → commit → push → pull request → CI checks → merge → deploy
```

More specifically:

```text
feature branch → pull request → GitHub Actions CI → merge to main → Cloudflare Pages production deploy
```

---

## What Has Not Been Added Yet

The following tools and concepts have intentionally not been added at this stage:

- Docker
- Terraform
- backend services
- database
- custom domain
- environment variables
- automated tests
- branch protection rules

Reason: the project is intentionally minimal so the core flow can be learned first.

---

## Next Steps

The next logical improvements for this training project are:

1. protect the `main` branch with required status checks
2. add a manual trigger (`workflow_dispatch`) to the CI workflow
3. add automated tests in addition to lint and build
4. continue improving the README as new phases are completed
5. later consider Docker and Terraform as next-stage DevOps topics





<!-- TEST -->