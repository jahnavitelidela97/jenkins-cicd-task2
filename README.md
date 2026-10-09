# DevOps Project: Infrastructure & Automation Setup (Task 2)

This repository contains the source configuration, automation scripts, and deployment files for Task 2. It follows standard Git branching and DevOps workflow best practices to ensure reliable version control and automated deployments.

---

## 📋 Table of Contents
- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Branching & Workflow Strategy](#branching--workflow-strategy)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Usage & Deployment](#usage--deployment)
- [Versioning & Release Management](#versioning--release-management)

---

## 🎯 Overview
The main goal of Task 2 is to manage version control and deployment pipelines for core application and infrastructure configurations. 

Key capabilities included in this repository:
- Containerized environment configuration using **Docker**.
- Multi-branch Git pipeline (`main`, `dev`, `feature/*`).
- Automated releases using Semantic Versioning tags (e.g., `v1.0.0`).

---

## 📁 Repository Structure

```text
├── Dockerfile          # Container configuration for application runtime
├── README.md           # Project documentation and setup instructions
├── DOCUMENTATION.md    # Step-by-step task execution log
├── .gitignore          # Rules for ignoring sensitive/unnecessary files
└── package.json        # Dependencies and project metadata (if applicable)

Branching & Workflow Strategy

We adhere to standard GitFlow conventions to maintain a clean history:

main: Production-ready code. Direct commits to main are restricted.

dev: Main integration branch for active development and staging.

feature/*: Short-lived branches used for individual tasks or bug fixes.

feature/setup-dockerfile ---> PR ---> dev ---> PR ---> main (Tag: v1.0.0)
⚙️ Prerequisites
Before getting started, ensure you have the following installed locally:

Git (v2.x or higher)

Docker Desktop

Node.js / npm (Optional for local testing)

🚀 Getting Started
1. Clone the Repository
Bash
git clone [https://github.com/jahnavitelidela97/task-4-git-devops-workflow.git](https://github.com/jahnavitelidela97/task-4-git-devops-workflow.git)
cd task-4-git-devops-workflow
2. Switch to Development Branch
Bash
git checkout dev
git pull origin dev
🐳 Usage & Deployment
Build Docker Image
To build the application container image using the Dockerfile:
bash
docker build -t task2-app:latest .
Run Container Locally
To run the container on port 3000:

Bash
docker run -d -p 3000:3000 --name task2-running-app task2-app:latest
Verify the application is running by opening http://localhost:3000 in your browser.

🏷️ Versioning & Release Management
We use annotated Git tags for release management following Semantic Versioning (SemVer):

v1.0.0: Initial stable production release with Docker application support.

To pull release tags locally:

Bash
git fetch --tags
git checkout v1.0.0

---

### Step-by-Step Instructions to Add/Update this `README.md`

Run these commands in your local terminal to update the file on GitHub:

```bash
# 1. Ensure you are on main branch
git checkout main
git pull origin main

# 2. Overwrite README.md with the content above (or edit the file manually in your editor)
# After pasting the markdown above into README.md, commit and push:

git add README.md
git commit -m "docs: update README.md for Task 2 documentation"
git push origin main
