# Build and Run the Application with Docker

This guide provides steps to build and run this repository which using a React application, a server API, and a MongoDB database using Docker.

## 1. Build Docker Images

### Build the React App

Run the following command to build the React frontend:

```sh
docker build -t react-app:1.0 ./client
```

### Build the server API

Run the following command to build the server API:

```sh
docker build -t api-server:1.0 ./server
```

### Pull Mongodb image

```sh
docker pull mongo:6
```

## 2. Run Containers Individually

### Create Docker Network

```sh
docker network create mern-app
```

You can run each service separately using Docker commands.

### Run MongoDB with Bind Mount (Optional)

```sh
docker run -d --name mongo -p 27017:27017 -v "${PWD}/mongo-data:/data/db" mongo:6
```

### Run database with volume

For better data persistence, use Docker volumes:

```sh
docker run -d --name mongo --network mern-app -p 27017:27017 -v mongo-data:/data/db -v mongo-config:/data/configdb mongo:6
```

### Run the server API

```sh
docker run -d --name api-server --network mern-app -p 5000:5000 api-server:1.0
```

## 3. Recommended: Run Everything with Docker Compose

Instead of running each service manually, it's recommended to use docker-compose, which simplifies management:

```sh
docker-compose up -d --build
```

This command will:

- Build the frontend and backend images if not already built.
- Start all services (React, API server, and MongoDB).
- Automatically handle networking between the containers.
