# Spring Boot API

This is a simple API showing how to properly create and document an API. 

## Tech Stack

This project is built with:

- Java 8 -> Language
- Spring Boot -> Main Framework
- MySql -> Main Database
- H2(In Memory DB) -> Test Database
- Logback -> Logging Framework
- ElasticSearch -> NoSQL Database used to store Logs asynchronously

## Requirements

To run this project you'll need to download the following:

- [Java](https://www.java.com/en/download/)
- [Gradle](https://gradle.org/install)
- [Docker](https://docs.docker.com/engine/installation/)

And if you want to run it stand alone you'll need to download [MySQL](https://www.mysql.com/downloads/) and configure the `application.properties` configuration file to point to the right db configuration(port, host, dbName, dbUser and dbPass)

## Running the Project With Docker

After having all the requirements, the first step is to generate the docker Image. To generate the docker image, go to the root of the project and run 

- `$ ./gradlew buildDocker`

Then you'll need to run the `docker.compose.yml` file that's on the directory `src/main/docker` through the following command: 

- `$ cd src/main/docker/`
- `$ docker-compose up`

After that you'll be able to start.

### Api Documentation (Swagger)

- If you access the root URL (` http://localhost:8080/ `) you'll be redirected to the API Documentation
- To access the api documentation directly, run the application and access : ` http://localhost:8080/swagger-ui.html `

- Through this documentation, you'll be able to make requests, as you'll see on the next topic.

### Endpoints

Currently it contains a basic crud of a User.

#### Adding a User (POST http://localhost:8080/users).

You can add a user doing a Post, here's an example using curl :

- `curl -H "Content-Type: application/json" -X POST -d '{"name":"Joao","role":"admin"}' http://localhost:8080/users`
- `curl -H "Content-Type: application/json" -X POST -d '{"name":"Zé","role":"marketing"}' http://localhost:8080/users`

#### Getting all Users (GET http://localhost:8080/users).

You can get all users doing a Get. It also works with multiple query parameters(examples: `/users?role=admin`, `/users?role=admin,marketing`, `/users?id=1,4&role=admin,marketing`). 

Here are some examples using curl :

- `curl -X GET http://localhost:8080/users`
- `curl -X GET http://localhost:8080/users?role=admin`
- `curl -X GET http://localhost:8080/users?role=admin,marketing`
- `curl -X GET http://localhost:8080/users?id=1,2&role=admin,marketing`

#### Updating a User (PUT http://localhost:8080/users/ID_OF_THE_USER).

Here's an example on how to change the property `name` of the user with the `id=1`:

- `curl -H "Content-Type: application/json" -X PUT -d '{"name":"First User"}' http://localhost:8080/users/1`

#### Deleting a User (PUT http://localhost:8080/users/ID_OF_THE_USER).

Here's an example on how to delete the user with the `id=4`:

- `curl -X DELETE http://localhost:8080/users/2`

## Access the api

After having the project running, you can access the api through [curl](https://curl.haxx.se/download.html) or any other http handler you prefer. 

It runs by default on the `http://localhost:8080/`.

