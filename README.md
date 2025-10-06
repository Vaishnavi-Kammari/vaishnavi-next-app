# Vaishnavi Next.js Dockerized App

This is a simple **Next.js application** containerized with **Docker**, automated with **GitHub Actions**, and deployable on **Kubernetes (Minikube)**.

---

## Project Structure

```
vaishnavi-next-app/
│
├── .github/workflows/docker-publish.yml  <-- *GitHub Actions workflow*
├── k8s/
│   ├── deployment.yaml  <-- *Kubernetes Deployment manifest*
│   └── service.yaml     <-- *Kubernetes Service manifest*
├── pages/
│   ├── api/hello.js     <-- *API route*
│   └── index.js         <-- *Main page*
├── public/              <-- *Static assets*
├── .dockerignore        <-- *Files to ignore in Docker build*
├── package.json         <-- *Node.js dependencies and scripts*
├── package-lock.json    <-- *Lock file for dependencies*
├── Dockerfile           <-- *Docker multi-stage build*
└── README.md            <-- *Project documentation*
```

---

## Setup

Clone the repository and install dependencies:

```bash
git clone https://github.com/Vaishnavi-Kammari/vaishnavi-next-app.git
cd vaishnavi-next-app
npm install
```

**Important:** Make sure Node.js and npm are installed.

---

## Local Run

Start the development server:

```bash
npm run dev
```

* Access the app at: **`http://localhost:3000`**
* Test API route: **`http://localhost:3000/api/hello`**

> **Highlight:** Local run is optional for submission, but helps verify the app.

---

## Docker Build & Run

Build the Docker image:

```bash
docker build -t vaishuk27/vaishnavi-next-app:latest .
```

Run the container:

```bash
docker run -p 3000:3000 vaishuk27/vaishnavi-next-app:latest
```

* Access the app at: **`http://localhost:3000`**

> **Highlight:** Docker image must use your **Docker Hub account `vaishuk27`**.

---

## GitHub Actions Workflow

* Builds the Docker image on every push to the **`main`** branch.
* Pushes the Docker image to Docker Hub under **`vaishuk27/vaishnavi-next-app:latest`**.

> **Important:** Add `DOCKER_HUB_PASSWORD` as a secret in GitHub repository settings.

---

## Minikube Deployment

Start Minikube:

```bash
minikube start
```

Apply Kubernetes manifests:

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

Access the service:

```bash
minikube service vaishnavi-next-app-service
```

> **Highlight:** Kubernetes deployment uses **2 replicas** and includes **readiness & liveness probes**.

---

## Notes

* GitHub repository: **`https://github.com/Vaishnavi-Kammari/vaishnavi-next-app`**
* Docker image pushed to Docker Hub: **`vaishuk27/vaishnavi-next-app:latest`**
* Multi-stage Dockerfile ensures **optimized production image size**.
* This project satisfies all **DevOps internship assessment requirements**.

---
