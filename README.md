# Go IAM – Docker Compose Environment

This repository provides a Docker Compose setup to run the full [Go IAM](https://github.com/melvinodsa/go-iam) authentication and authorization platform along with its admin UI and dependencies (MongoDB and Redis). This setup is designed primarily for **local development and testing**.

---

## ✨ What’s Included

| Service        | Description                                             |
| -------------- | ------------------------------------------------------- |
| `mongo-go-iam` | MongoDB instance for storing IAM data                   |
| `redis-go-iam` | (Optional) Redis instance for caching tokens            |
| `go-iam`       | Backend authentication and authorization service (Go)   |
| `go-iam-ui`    | Admin UI to manage tenants, roles, users, and resources |

---

## 🚀 Getting Started

### 1. Clone this repository

```bash
git clone https://github.com/<your-org-or-username>/go-iam-docker.git
cd go-iam-docker
```

### 2. Prepare .env file

Rename the example file or create your own .env

```bash
cp sample.env .env
```

Update any values as needed. Here's a sample configuration:

```env
SERVER_HOST=127.0.0.1
SERVER_PORT=3000
DEPLOYMENT_ENVIRONMENT=local
DEPLOYMENT_NAME=Go IAM
LOGGER_LEVEL=2
DB_HOST=mongodb://mongo-go-iam
ENCRYPTER_KEY=
REDIS_HOST=redis-go-iam:6379
REDIS_DB=0
REDIS_PASSWORD=
JWT_SECRET=abcd
ENABLE_REDIS=true
TOKEN_CACHE_TTL_IN_MINUTES=1440
AUTH_PROVIDER_REFETCH_INTERVAL_IN_MINUTES=1
VITE_API_SERVER=http://localhost:3000
```

### 3. Build and Start the Environment

```bash
docker compose up -d
```

This will build the backend (go-iam) and frontend (go-iam-ui) containers, and start MongoDB and Redis.

## 🖥️ Access the UI

Once all services are up:

Admin UI: http://localhost:4173

API (Go IAM): http://localhost:3000
