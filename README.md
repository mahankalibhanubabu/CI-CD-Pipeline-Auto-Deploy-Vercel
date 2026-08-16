# 🚀 CI/CD Pipeline — Automated Next.js Deployment to Vercel

<p align="center">
  <img src="https://img.shields.io/badge/CI%2FCD-Jenkins-red?style=for-the-badge&logo=jenkins&logoColor=white" />
  <img src="https://img.shields.io/badge/Frontend-Next.js-black?style=for-the-badge&logo=next.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Runtime-Node.js-green?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Deployment-Vercel-black?style=for-the-badge&logo=vercel&logoColor=white" />
  <img src="https://img.shields.io/badge/Automation-CI%2FCD-blue?style=for-the-badge&logo=githubactions&logoColor=white" />
</p>

<p align="center">
  <b>Automated build and production deployment pipeline using Jenkins + Vercel</b>
</p>

<p align="center">
  <a href="https://my-app-nextjs-pipeline.vercel.app">
    <img src="https://img.shields.io/badge/🌐%20Live%20Demo-Visit%20Application-success?style=for-the-badge" />
  </a>
  <a href="https://github.com/mahankalibhanubabu/CI-CD-Pipeline-Auto-Deploy-Vercel">
    <img src="https://img.shields.io/badge/📂%20Source%20Code-GitHub-black?style=for-the-badge&logo=github" />
  </a>
</p>

---

## 🎯 Project Overview

This project demonstrates a **real-world CI/CD workflow** for a Next.js application using **Jenkins as the automation server** and **Vercel as the production deployment platform**.

Instead of manually installing dependencies, building the application, and deploying it after every change, Jenkins automates the deployment workflow.

### 🔄 Pipeline Flow

```text
                 ┌──────────────────┐
                 │   Developer      │
                 │   Code Changes   │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │      GitHub      │
                 │ Source Control   │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │     Jenkins      │
                 │   CI/CD Server   │
                 └────────┬─────────┘
                          │
                 ┌────────┴─────────┐
                 │                  │
                 ▼                  ▼
        ┌────────────────┐   ┌────────────────┐
        │ Install        │   │ Build          │
        │ npm install    │──▶│ npm run build  │
        └────────────────┘   └───────┬────────┘
                                     │
                                     ▼
                            ┌─────────────────┐
                            │ Vercel          │
                            │ Production      │
                            │ Deployment      │
                            └─────────────────┘
```

---

## ⚡ What This Project Demonstrates

* ✅ CI/CD pipeline automation
* ✅ Jenkins Declarative Pipeline
* ✅ Automated dependency installation
* ✅ Automated production builds
* ✅ Secure credential handling through Jenkins
* ✅ Vercel CLI-based deployment
* ✅ Next.js production deployment
* ✅ Infrastructure-independent deployment workflow
* ✅ Repeatable and consistent releases

---

## 🛠️ Tech Stack

| Category        | Technology   |
| --------------- | ------------ |
| Frontend        | Next.js      |
| UI Library      | React        |
| Language        | TypeScript   |
| Styling         | Tailwind CSS |
| CI/CD           | Jenkins      |
| Source Control  | Git & GitHub |
| Deployment      | Vercel       |
| Runtime         | Node.js      |
| Package Manager | npm          |

---

## 🔥 Jenkins Pipeline

The project uses a **Jenkins Declarative Pipeline** with four stages:

### 1️⃣ Install

Installs all project dependencies.

```bash
npm install
```

### 2️⃣ Test

The pipeline currently skips automated tests because the project does not contain a dedicated test script.

```text
Skipping tests - no test script found
```

### 3️⃣ Build

Creates the production-ready Next.js build.

```bash
npm run build
```

### 4️⃣ Deploy

Deploys the production build to Vercel using the Vercel CLI.

```bash
npx vercel --prod --yes --token=%VERCEL_TOKEN%
```

The Vercel token is stored as a **Jenkins credential** rather than hard-coded into the pipeline.

---

## 🔐 Secure Credential Management

The deployment token is handled through Jenkins credentials:

```groovy
environment {
    VERCEL_TOKEN = credentials('vercel_token')
}
```

This prevents the sensitive Vercel token from being directly written into the source code.

> ⚠️ Never commit Vercel tokens, API keys, passwords, or other secrets to GitHub.

---

## 📁 Project Structure

```text
CI-CD-Pipeline-Auto-Deploy-Vercel/
│
├── app/
│   ├── favicon.ico
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
│
├── public/
│
├── .gitignore
├── Jenkinsfile
├── next.config.ts
├── package.json
├── package-lock.json
├── postcss.config.mjs
├── tsconfig.json
└── README.md
```

---

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/mahankalibhanubabu/CI-CD-Pipeline-Auto-Deploy-Vercel.git
```

### 2. Enter the project

```bash
cd CI-CD-Pipeline-Auto-Deploy-Vercel
```

### 3. Install dependencies

```bash
npm install
```

### 4. Start development server

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

---

## 🏗️ Production Build

To verify the application locally before deployment:

```bash
npm run build
```

Then start the production server:

```bash
npm start
```

---

## ⚙️ Jenkins Configuration

### Prerequisites

Install/configure:

* Jenkins
* Node.js
* npm
* Git
* Vercel CLI
* Jenkins Credentials

### Jenkins Credential

Create a Jenkins credential with:

```text
ID: vercel_token
Type: Secret Text
Value: <YOUR_VERCEL_TOKEN>
```

The pipeline accesses this credential through:

```groovy
credentials('vercel_token')
```

---

## 🔁 CI/CD Workflow

```text
Code Change
     │
     ▼
   GitHub
     │
     ▼
  Jenkins
     │
     ├── Install Dependencies
     │
     ├── Validate / Test
     │
     ├── Build Application
     │
     └── Deploy
           │
           ▼
         Vercel
           │
           ▼
    Production Application
```

The goal is simple:

> **Commit code → automate the pipeline → build → deploy.**

---

## 🌐 Live Application

### Production

🚀 **[Open Live Application](https://my-app-nextjs-pipeline.vercel.app)**

The deployed application is currently accessible through Vercel.

---

## 📊 Pipeline Stages

| Stage      | Purpose                 | Command             |
| ---------- | ----------------------- | ------------------- |
| 📦 Install | Install dependencies    | `npm install`       |
| 🧪 Test    | Test stage / validation | Configurable        |
| 🏗️ Build  | Create production build | `npm run build`     |
| 🚀 Deploy  | Deploy to Vercel        | `npx vercel --prod` |

---

## 💡 Why I Built This

Manual deployments are repetitive and error-prone.

This project was built to understand how a **CI/CD pipeline can automate application delivery** from source code to production.

It demonstrates practical concepts such as:

* Pipeline as Code
* CI/CD automation
* Jenkins stages
* Secret management
* Production builds
* Automated cloud deployment
* Repeatable release processes

---

## 🔮 Future Improvements

The current pipeline is functional, but it can be made significantly stronger.

### Planned Improvements

* [ ] Add automated unit tests
* [ ] Add ESLint / code-quality checks
* [ ] Add SonarQube integration
* [ ] Add security scanning with Trivy
* [ ] Add Docker-based build environment
* [ ] Add Jenkins webhook-based triggering
* [ ] Add deployment notifications
* [ ] Add rollback strategy
* [ ] Add preview deployments for pull requests
* [ ] Add production deployment approval
* [ ] Add pipeline status badges

---

## 🧠 DevOps Concepts Practiced

```text
Source Control
      ↓
Pipeline as Code
      ↓
Continuous Integration
      ↓
Automated Build
      ↓
Credential Management
      ↓
Continuous Deployment
      ↓
Production Release
```

---

## 👨‍💻 Author

### Bhanu Babu

**DevOps & Workload Automation Engineer | Cloud & Full-Stack Developer**

Interested in:

`DevOps` • `Cloud` • `CI/CD` • `Jenkins` • `Docker` • `Kubernetes` • `Automation` • `Full-Stack Development`

<p align="left">
  <a href="https://www.linkedin.com/in/mahankali-bhanubabu-devops-developer/">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin" />
  </a>
</p>

---

<p align="center">

### ⚙️ Automate → Build → Deploy → Repeat 🚀

</p>

<p align="center">
  <i>Built to learn. Automated to scale.</i>
</p>
