DevOps Internship — Task 1: Node.js App Dockerization & CI/CD 🚀

- Overview
This project demonstrates the complete DevOps workflow for a simple Node.js application. It covers:
1. Setting up the development environment.
2. Building and running a Node.js app locally.
3. Dockerizing the application.
4. Automating Docker image build and deployment using GitHub Actions.
5. This task reflects Phase 1 to Phase 3 of the internship roadmap, highlighting hands-on learning in DevOps tools and processes.

- Phase 1 — Setup & Basics ⚙️
Objective: Prepare the environment and understand a simple Node.js app.

Steps Completed:
  Installed essential tools:
  Node.js – Backend runtime.
  Git – Version control.
  Docker Desktop – Containerization.
  Created a GitHub account and initialized a repository.
  Built a simple Node.js application:
  index.js runs a basic HTTP server.
  Tested locally using node index.js.
  Learned basic Git operations:
  git init, git add, git commit, git push.
  
Outcome: Development environment ready, basic Node.js app running, and GitHub repository initialized.

- Phase 2 — Dockerizing the App 🐳

Objective: Containerize the Node.js application for consistent deployment.

Steps Completed:
  Created a Dockerfile:
  Defined base image (node:18-alpine).
  Copied project files.
  Installed dependencies using npm install.
  Exposed port 3000.
  Defined startup command (node index.js).
  Built Docker image locally:
    docker build -t girishpatil2102/task1-devops-internship:latest .
  Ran Docker container locally:
    docker run -p 3000:3000 girishpatil2102/task1-devops-internship:latest
  Pushed the Docker image to Docker Hub for sharing and deployment.

Outcome: Node.js app successfully containerized and tested in Docker.

- Phase 3 — CI/CD with GitHub Actions ⚡

Objective: Automate build, test, and Docker image deployment.

Steps Completed:
  Created .github/workflows/main.yml.
  Defined workflow jobs:
  Checkout code from GitHub.
  Set up Node.js environment.
  Install dependencies and run tests.
  Log in to Docker Hub.
  Build and push Docker image automatically.
  Verified automation by pushing code changes to GitHub.
  Observed automatic build and Docker image deployment in the Actions tab.

Outcome: Fully automated CI/CD pipeline is functional, ensuring changes trigger automated builds and deployments.



CI/CD Pipeline:

  Every push triggers the GitHub Actions workflow.
  
  Docker image is automatically built and pushed to Docker Hub.




Learnings & Skills Gained

  Node.js project setup and dependency management.
  
  Containerization concepts with Docker.
  
  Automated CI/CD pipelines using GitHub Actions.
  
  Hands-on integration of GitHub and Docker Hub.

ANSWER FOR THE INTERVIEW QUESTIONS:-

1. What is CI/CD?

CI/CD stands for Continuous Integration and Continuous Deployment/Delivery.

Continuous Integration (CI): Developers frequently merge code changes into a shared repository. Automated builds and tests run to ensure code quality.

Continuous Deployment/Delivery (CD): Code changes are automatically deployed to staging or production environments. CD reduces manual intervention and ensures faster, reliable releases.
Benefit: Faster development cycles, fewer integration issues, and higher deployment reliability.

2. How do GitHub Actions work?

GitHub Actions is a CI/CD automation tool integrated into GitHub repositories.

Workflows are defined in .github/workflows/*.yml files.

A workflow consists of events, jobs, and steps.

Event triggers: e.g., push, pull_request.

Jobs: Units of work that run on runners.

Steps: Individual commands or actions executed sequentially within a job.

GitHub Actions can automate builds, tests, and deployments.

3. What are runners?

Runners are servers that execute workflows in GitHub Actions.

Types of runners:

GitHub-hosted runners: Managed by GitHub, automatically provisioned and discarded after job completion.

Self-hosted runners: Managed by the user, run on custom machines or servers.

Role: They pick up jobs and run each step as defined in the workflow.

4. Difference between jobs and steps
Jobs

A job is a unit of work in a workflow.

Jobs can run in parallel or sequentially.	

Example: Build, Test, Deploy.	

Steps

A step is a single command/action within a job.

Steps within a job always run sequentially.

Example: checkout code, install dependencies, run tests.

6. How to secure secrets in GitHub Actions?

GitHub allows storing sensitive data (API keys, Docker credentials) as secrets in the repository settings:

Repository → Settings → Secrets and Variables → Actions → New Repository Secret.

Access secrets in workflow using secrets.NAME:

- name: Login to Docker Hub
  run: docker login -u ${{ secrets.DOCKER_USERNAME }} -p ${{ secrets.DOCKER_PASSWORD }}


Best practice: Never hardcode secrets in the workflow file. Use secrets and environment variables.

6. How to handle deployment errors?

Check logs: GitHub Actions provides detailed logs for each step.

Fail fast: Stop deployment if a critical step fails using fail-fast: true.

Retry strategies: Some steps (like API calls) can have retry logic.

Notifications: Configure notifications (email, Slack) for failures.

Rollbacks: Use previous stable Docker image or version to roll back deployment.

7. Explain the Docker build-push workflow

Build: Create a Docker image from the Dockerfile.

docker build -t username/appname:tag .


Test/run locally: Verify the image works.

docker run -p 3000:3000 username/appname:tag


Tag: Optional, for versioning images.

docker tag username/appname:tag username/appname:latest


Push: Upload the image to Docker Hub or other container registry.

docker push username/appname:tag


Use in CI/CD: Automate the build and push in GitHub Actions.

8. How can you test a CI/CD pipeline locally?

Using tools like:

Act
 – Runs GitHub Actions workflows locally.

Docker-based testing: Run the workflow commands inside a Docker container.

Steps:

Install Act (brew install act or download binary).

Navigate to repository with .github/workflows.

Run act push or act workflow_name.yml.

Benefit: Validate CI/CD logic without pushing to GitHub, saving time.

