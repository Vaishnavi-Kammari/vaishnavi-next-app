# Next.js Application with Docker, GitHub Actions, and Kubernetes

This project is a Next.js application that is containerized using Docker, automated with GitHub Actions, and deployed on Kubernetes using Minikube. This README provides comprehensive documentation on how to set up, run, and deploy the application.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Running the Application Locally](#running-the-application-locally)
- [Dockerization](#dockerization)
- [GitHub Actions](#github-actions)
- [Kubernetes Deployment](#kubernetes-deployment)
- [Accessing the Application](#accessing-the-application)

## Prerequisites

Before you begin, ensure you have the following installed:

- Node.js (version 14 or later)
- Docker
- Docker Compose
- Minikube
- kubectl
- GitHub account

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd nextjs-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

## Running the Application Locally

To run the application locally, use the following command:

```bash
npm run dev
```

This will start the Next.js application in development mode. You can access it at `http://localhost:3000`.

## Dockerization

To build the Docker image for the application, run:

```bash
docker build -t nextjs-app .
```

To run the Docker container, use:

```bash
docker run -p 3000:3000 nextjs-app
```

## GitHub Actions

The project includes a GitHub Actions workflow located at `.github/workflows/ci.yml`. This workflow automates the following processes:

- Builds the Docker image on pushes to the main branch.
- Pushes the image to GitHub Container Registry (GHCR).
- Tags the image appropriately.

## Kubernetes Deployment

To deploy the application on Kubernetes using Minikube, follow these steps:

1. Start Minikube:
   ```bash
   minikube start
   ```

2. Apply the deployment configuration:
   ```bash
   kubectl apply -f k8s/deployment.yaml
   ```

3. Apply the service configuration:
   ```bash
   kubectl apply -f k8s/service.yaml
   ```

## Accessing the Application

To access the deployed application, you can use the following command to get the URL:

```bash
minikube service <service-name> --url
```

Replace `<service-name>` with the name defined in your `service.yaml` file.

## Conclusion

This README provides a comprehensive overview of setting up, running, and deploying the Next.js application. For further customization and development, refer to the Next.js documentation and the respective files in this project.
