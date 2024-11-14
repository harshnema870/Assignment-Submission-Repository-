# Assignment-Submission-Repository-
This Project is submitted as a Flipr Campus Drive DevOps Assignment. 
The revised `README.md` file provides clear guidance on using Docker to run the full-stack application locally, as well as instructions for each essential file:

---

# **Full-Stack Application Containerization with Docker**

This project demonstrates a full-stack application setup using Docker. The app includes a **React frontend**, **Express backend**, and **MongoDB database**, all containerized. With **Docker Compose**, you can easily manage and run all services simultaneously, while a shell script automates build, push, and deployment.

## **Project Structure**

- **Frontend Dockerfile**: Builds the React frontend.
- **Backend Dockerfile**: Builds the Express backend.
- **Docker Compose File**: Manages the frontend, backend, and MongoDB containers.
- **Shell Script**: Automates Docker build, push, and run commands.

## **Table of Contents**

- [Getting Started](#getting-started)
- [Docker Files](#docker-files)
  - [Frontend Dockerfile](#frontend-dockerfile)
  - [Backend Dockerfile](#backend-dockerfile)
  - [Docker Compose File](#docker-compose-file)
  - [Shell Script](#shell-script)
- [Running the Application](#running-the-application)
- [Testing and Access](#testing-and-access)
- [Troubleshooting](#troubleshooting)

---

## **Getting Started**

To run the application locally, you’ll need:

- **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
- **Docker Hub Account**: Optional if you want to push images to Docker Hub.

Clone the repository and navigate to the project root:

```bash
git clone https://github.com/fliprlab/devops-task
cd devops-task
```

## **Docker Files**

### **1. Frontend Dockerfile**

The **frontend Dockerfile** builds and serves the React application:

- Based on a Node.js image.
- Copies project files, installs dependencies, and builds the frontend.
- Uses a lightweight server to serve built files.

### **2. Backend Dockerfile**

The **backend Dockerfile** builds and runs the Express backend:

- Based on a Node.js image.
- Copies project files, installs dependencies, exposes a port, and starts the backend server.

### **3. Docker Compose File**

The **docker-compose.yml** file orchestrates the three services:

- **Frontend**: Maps to the frontend Dockerfile, exposes port `3000`.
- **Backend**: Maps to the backend Dockerfile, exposes port `5000`.
- **MongoDB**: Uses an official MongoDB image, exposes port `27017`.

### **4. Shell Script**

The **shell script (`deploy.sh`)** automates the following:

- Builds and tags Docker images for frontend and backend.
- Pushes images to Docker Hub (if configured).
- Launches Docker Compose to start the application.

Make the script executable:

```bash
chmod +x deploy.sh
```

Run the script:

```bash
./deploy.sh
```

## **Running the Application**

### **Option 1: Using Docker Compose**

1. **Build and start the application**:

   ```bash
   docker-compose up --build -d
   ```

   This will:
   - Build frontend and backend Docker images.
   - Start containers for frontend, backend, and MongoDB.
   - Set up network connections between containers.

2. **Stop the application**:

   ```bash
   docker-compose down
   ```

### **Option 2: Using the Shell Script**

Run `deploy.sh` to automate build, push, and deployment:

```bash
./deploy.sh
```

This will:
- Build and push images to Docker Hub (if specified).
- Run `docker-compose up` to start the application.

> **Note**: Set up your Docker Hub credentials in the script to push images.

## **Testing and Access**

Access the running services:

- **Frontend**: [http://localhost:3000](http://localhost:3000) — React frontend.
- **Backend**: [http://localhost:5000](http://localhost:5000) — Express backend.
- **API Endpoint**: [http://localhost:5000/api/users](http://localhost:5000/api/users) — `/api/users` endpoint.

## **Troubleshooting**

### **Common Issues**

- **Cannot GET /**: Ensure API paths are correct (e.g., `/api/users`).
- **MongoDB Connection Errors**: Verify MongoDB is running and accessible at the correct URI (`MONGO_URI`).

### **Rebuilding Containers**

After code changes, rebuild the images:

```bash
docker-compose up --build -d
```

---

