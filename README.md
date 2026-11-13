# Node.js CI/CD Demo

A simple Node.js backend built with Express to practice **Continuous Integration (CI)** and **Continuous Deployment (CD)** using GitHub Actions, Docker, and AWS EC2.

## Tech Stack

- Node.js 22
- Express.js
- Docker
- GitHub Actions
- AWS EC2 (deployment target)

## Project Structure

```text
node-cicd-demo/
├── src/
│   ├── app.js
│   └── server.js
├── tests/
│   └── app.test.js
├── .github/
│   └── workflows/
│       └── ci.yml
├── Dockerfile
├── .dockerignore
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 22
- npm
- Docker (optional for local development)

### Installation

Clone the repository:

```bash
git clone <your-repository-url>
cd node-cicd-demo
```

Install dependencies:

```bash
npm ci
```

Start the server:

```bash
npm start
```

The server will be available at:

`http://localhost:3000`

## API Endpoints

### GET /

Returns a welcome message.

**Example response:**

```json
{
  "message": "Hello from Node.js CI/CD!",
  "version": "1.0.0"
}
```

### GET /health

Returns the application's health status and uptime.

**Example response:**

```json
{
  "status": "healthy",
  "uptime": 120.5
}
```

## Running Tests

Run automated tests:

```bash
npm test
```

Tests use Node.js's built-in test runner and Supertest.

## Docker

Build the Docker image:

```bash
docker build -t node-cicd-demo .
```

Run the container:

```bash
docker run -d \
  --name node-cicd \
  -p 3000:3000 \
  node-cicd-demo
```

Verify the deployment:

```bash
curl http://localhost:3000/health
```

View container logs:

```bash
docker logs node-cicd
```

Stop and remove the container:

```bash
docker stop node-cicd
docker rm node-cicd
```

## CI/CD Pipeline

### Continuous Integration (Implemented)

GitHub Actions automatically runs on pushes to `main` and pull requests targeting `main`.

Pipeline steps:

1. Checkout repository
2. Set up Node.js
3. Install dependencies
