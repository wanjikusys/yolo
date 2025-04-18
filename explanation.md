# Dockerized E-Commerce App - IP2 Explanation

## 1. Base Image Choices
- **Backend**: Used `node:18-alpine` to minimize image size while maintaining compatibility with Node.js dependencies.
- **Frontend**: Based on `node:18-alpine` for builds and `nginx:alpine` for serving the static files.
- **Database**: Used official `mongo:latest` for stability and built-in volume support.

## 2. Dockerfile Directives
- `WORKDIR` defines the default folder for container operations.
- `COPY` brings in project files.
- `RUN` installs dependencies (only production for backend).
- `CMD` or `ENTRYPOINT` launches the app.

## 3. Docker-Compose Networking
- All services use a shared `bridge` network called `app-network`.
- Ports:
  - Frontend exposed on `3000:80`
  - Backend exposed on `5000:5000`
  - Mongo on `27017:27017`

## 4. Volume Definitions
- MongoDB uses volumes for persistent data:
  ```yaml
  volumes:
    - mongo-data:/data/db

## 5. Git Workflow

Used Git to track the progress of this project from setup to deployment.

- **Initialized Git** in the project directory using `git init`.
- **.gitignore** file added to ignore unnecessary files like `node_modules`, environment configs, and logs.
- Made **at least 10 descriptive commits**, for example:
  - `init backend Dockerfile`
  - `add docker-compose.yml`
  - `set up MongoDB service`
  - `build and push Docker images`
- Created a clean folder structure:
  - `/backend`
  - `/client`
  - `docker-compose.yml`
  - `.gitignore`
  - `README.md`

All these steps are visible in the commit history of the repo. This helped me keep track of what was done and troubleshoot easily.

Finally, pushed my code to GitHub:  
👉 [GitHub Repository Link](https://github.com/wanjikusys)

