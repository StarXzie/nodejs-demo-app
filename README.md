# Node.js Demo App — CI/CD with GitHub Actions

## Overview
A sample Node.js application with an automated CI/CD pipeline using GitHub Actions and Docker.

Whenever code is pushed to the `main` branch, GitHub Actions automatically runs tests, builds a Docker image, and pushes the image to Docker Hub.

## Technologies Used
- Node.js
- Express.js
- Docker
- Git and GitHub
- GitHub Actions
- Docker Hub

## Project Structure

```text
nodejs-demo-app/
├── .github/
│   └── workflows/
│       └── main.yml
├── test/
│   └── app.test.js
├── app.js
├── server.js
├── package.json
├── package-lock.json
├── Dockerfile
├── .dockerignore
└── .gitignore
```

## CI/CD Pipeline

The workflow consists of two jobs:

### 1. Test
- Checks out the repository.
- Sets up Node.js.
- Installs dependencies.
- Runs automated tests using `npm test`.

### 2. Build and Push
- Runs only after the test job succeeds.
- Logs in to Docker Hub using GitHub Secrets.
- Builds the Docker image.
- Pushes the image to Docker Hub with the `latest` tag.

## Security

Docker Hub credentials are stored securely in GitHub Actions Secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

No credentials are hardcoded in the source code or workflow.

## Running Locally

Install dependencies:

```bash
npm install
```

Run tests:

```bash
npm test
```

Start the application:

```bash
node server.js
```

Open `http://localhost:3000` in your browser.

## Docker

Build the image:

```bash
docker build -t nodejs-demo-app .
```

Run the container:

```bash
docker run -p 3000:3000 nodejs-demo-app
```

## Deployment

Docker Hub image:

`starzie/nodejs-demo-app:latest`

## Result

Successfully implemented an automated CI/CD pipeline using GitHub Actions, including automated testing, Docker image building, and Docker Hub deployment.

The workflow is triggered automatically on every push to the `main` branch.
