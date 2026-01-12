# Image Cluster AI – Full Deployment

Docker Compose project to deploy the **Image Cluster AI system** (API + Web Client) with optional sample images for testing.

> **Proof of Concept (PoC)**  
> This repository focuses on making it easy to run the full AI-powered image clustering system locally, with a modular architecture that can be extended.  
> It is intended for experimentation and demonstration, not for production use.


---

## 1. Purpose

This project provides:

1. **One-command full deployment** of API and Web Client using Docker Compose
2. A ready-to-use **folder of sample images** for testing clustering and AI descriptions
3. Option to deploy **only the API** or **only the Web Client** if desired

It serves as the central entry point for anyone who wants to explore the system end-to-end.

---

## 2. Repository Structure

This web client does **not** perform any AI processing by itself.  
All AI and ML logic lives in the backend API.

```text
image-cluster-ai-deploy/
├── docker-compose.yml          # Compose file to deploy full system
├── .env                        # Optional environment overrides
├── sample-images/              # Images for testing
├── image-cluster-ai-api/       # API sub-repository (clone inside this folder)
├── image-cluster-ai-web/       # Web Client sub-repository (clone inside this folder)
└── README.md
```

Note: image-cluster-ai-api and image-cluster-ai-web must be cloned inside this repository or downloaded manually.

---

## 3. Environment Variables

You can override ports and configuration via the .env file:

```text
COMPOSE_PROJECT_NAME=image-cluster-ai

# Ports exposed on the host machine
API_HOST_PORT=8001
WEB_HOST_PORT=8082

# API URL used by the web client during build
API_URL=http://image-cluster-ai-api:${API_HOST_PORT}
```

- The .env file is optional; defaults are provided in docker-compose.yml.

- Changing API_HOST_PORT or WEB_HOST_PORT is safe.

- The API_URL should not be changed unless you know what you are doing.

---

## 4. Full Deployment (API + Web Client + Samples)

#### Recommended: Using Git

1. Clone this deploy repository:

```bash
git clone https://github.com/rafael-dev-com/image-cluster-ai-deploy
cd image-cluster-ai-deploy
```

2. Inside the deploy folder, clone the sub-repositories:
```bash
git clone https://github.com/rafael-dev-com/image-cluster-ai-api
git clone https://github.com/rafael-dev-com/image-cluster-ai-web
```
3. Start the services with Docker Compose:
```bash
docker-compose up --build
```
- This will build and start all services.

- The web client will run at http://localhost:8082.

- Sample images can be found in sample-images/ for quick testing.

#### To stop all services:
```bash
docker-compose down
```
---

### Alternative: Manual download

If you prefer not to use git, you can also download the repositories manually:

- Place repo-api and repo-web inside the deploy folder.

- Make sure the folder structure matches:
```bash
image-cluster-ai-deploy/
├── image-cluster-ai-api/
├── image-cluster-ai-web/
└── docker-compose.yml
```
- Then, from inside the `image-cluster-ai-deploy` folder, run:
:
```bash
docker-compose up --build
```

The web client will run at http://localhost:8082.

This method works the same way; git just makes it more convenient.

---
## 5. Related repositories

This API is part of a larger system:

- [Backend API - image-cluster-ai-api](https://github.com/rafael-dev-com/image-cluster-ai-api)

- [Web client - image-cluster-ai-web](https://github.com/rafael-dev-com/image-cluster-ai-web)

---

## 6. Future improvements

- Preloaded sample images in Docker volume

- Configurable environment variables at runtime

- Health checks and readiness probes

- Optional HTTPS support

- CI/CD for automated builds and deployment

---

## 7. Quick Start Summary
```bash
# Clone the deploy repo
git clone https://github.com/rafael-dev-com/image-cluster-ai-deploy
cd image-cluster-ai-deploy

# Clone sub-repos
git clone https://github.com/rafael-dev-com/image-cluster-ai-api
git clone https://github.com/rafael-dev-com/image-cluster-ai-web

# Run everything
docker-compose up --build

# Access the web client
http://localhost:8082
```