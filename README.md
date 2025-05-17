# DevOps: Docker Compose Multi-Service Application

## Overview
This project demonstrates a multi-service application containerized with Docker and orchestrated using Docker Compose.  
It includes:
- **backend** — Go REST API service
- **frontend** — Vue.js SPA
- **nginx** — Reverse proxy and static file server

## Project Structure
```plaintext
├── backend                 # Go backend
│   ├── cmd
│   │   └── api
│   ├── Dockerfile          # Dockerfile for backend. Used to build the backend binary
│   ├── go.mod
│   ├── go.sum
│   └── internal
│       ├── logger
│       └── store
├── docker-compose.yml      # Docker Compose file to run the application
├── frontend                # Vue.js frontend
│   ├── babel.config.js
│   ├── Dockerfile          # Dockerfile for frontend. Used to build the frontend static files
│   ├── package-lock.json
│   ├── package.json
│   ├── public
│   │   ├── _redirects
│   │   ├── favicon.ico
│   │   └── index.html
│   ├── src
│   │   ├── App.vue
│   │   ├── assets
│   │   ├── components
│   │   ├── main.ts
│   │   ├── models
│   │   ├── router
│   │   ├── services
│   │   ├── shims-vue.d.ts
│   │   ├── shims-vuex.d.ts
│   │   ├── store
│   │   ├── typings
│   │   └── views
│   ├── tsconfig.json
│   └── vue.config.js
├── nginx                   # Nginx configuration    
│   ├── Dockerfile          # Dockerfile for nginx. Used to build custom nginx image
│   └── nginx.conf          # Nginx configuration file
└── README.md
```

## Quick Start

1. **Set up environment variables:**  
   Create a `.env` file based on `.env.example` and set your Docker Hub username:
   ```
   DOCKER_REGISTRY=your_dockerhub_username
   ```

2. **Build and run all services:**
   ```
   docker compose up --build
   ```

3. **Access the application:**
   - Frontend: [http://localhost/momo-store/](http://localhost/momo-store/)
   - Backend API: [http://localhost/api/](http://localhost/api/)

## Useful Commands

- Build and run:  
  ```
  docker compose up --build
  ```
- Stop all services:  
  ```
  docker compose down
  ```

## Features

- Non-root users in containers
- Dropped Linux capabilities for security
- Healthchecks, resource limits, restart policies
- Isolated networks for services
- Multi-stage builds for smaller images
- Custom Nginx image for static file serving
