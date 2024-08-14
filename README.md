current Dockerfile is using Node.js version 8, which is outdated and does not support modern JavaScript syntax, including the catch block without a parameter that caused the error earlier. To resolve this and ensure compatibility with the latest React and JavaScript features, you should update the Node.js version to a more recent one, such as Node.js 14 or 16.

To build
- make sure docker daemon is up
- docker-compose up -d

 the environment variables for POSTGRES_DB, POSTGRES_USER, and POSTGRES_PASSWORD in your docker-compose.yml file should match those defined in your Dockerfile. This ensures that the PostgreSQL container is configured consistently across your Dockerfile and Docker Compose setup.

 In the docker-compose.yml, the environment section for the postgres service should match the environment variables in your Dockerfile

Port Mapping: Ensure the port mapping (5432:5432) is correctly set in docker-compose.yml. You had 5432 without specifying :5432, which might default to the internal port.

Database Initialization: The COPY psql_dump.sql /docker-entrypoint-initdb.d/ command in the Dockerfile will initialize the database with the contents of psql_dump.sql when the container starts.

Deprecation: The links option is deprecated in newer versions of Docker Compose. You can rely on depends_on for service ordering, as Docker Compose manages networking by default.

Access the React application at http://localhost:3000/ after starting the container to verify everything works correctly.
# TODO-Fullstack-App-Go-Gin-Postgres-React
![Test Coverage](backend/api/coverage_badge.png)

This fullstack application creates a TODO List Web Page using the Go/Gin/Postgres/React Stack.

![Screen Shot](App.png)

## Starting the application

In the project root, run: 
```
docker-compose build 
docker-compose up
```

## Go server

Go is used to spin up the server, define routing, and interact with the database.

## Gin router

Gin is used to define the TODO API with functionality such as:

1. Listing all TODO items.
2. Creating a new TODO item and adding to the database.
3. Updating a TODO item with its completed condition.
4. Deleting a TODO item from the database.
5. Later being able to filter TODO items.

## Postgres Database

Postgres is used to store the TODO items by saving rows in as id, item-text, and done boolean condition.

## React

React is used here to create the frontend fully responsive application on the client side and is built using components.
