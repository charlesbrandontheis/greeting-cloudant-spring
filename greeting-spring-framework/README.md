# Spring Framework Greeting application

This application shows how to connect to a Cloudant database using the new `@EnableCloudant` annotation provided by the [Cloudant Spring Library](https://github.com/cloudant-labs/cloudant-springofficial). The library provides Spring capabilities on top of the official [Cloudant Java library](https://github.com/cloudant/java-cloudant).

## Pre-requisites

* [Apache Maven](https://maven.apache.org/)
* [Docker](https://www.docker.com/)

## Building and running

Before running create a `src/main/resources/cloudant.properties` file with your Cloudant credentials:

~~~
cloudant.username=cloudantUsername
cloudant.password=cloudantPassword
cloudant.url=cloudantUrl
cloudant.db=databaseName
~~~

### To build:

* `mvn clean install`

### When run as a war (e.g. Run On Server in Spring Tool Suite): 

Available endpoints:

* `http://localhost:8080/demo/databases`
* `http://localhost:8080/demo/greeting`
* `http://localhost:8080/demo/greeting/{id}`

Create a new greeting by supplying some content:

`curl -H "Content-Type: application/json" -d '{"content":"test123"}' http://localhost:8080/demo/greeting`

Ask for all known greetings:

`curl http://localhost:8080/demo/greeting`

Ask for a particular greeting:

`curl http://localhost:8080/demo/greeting/ID`

Delete a greeting:

`curl -X DELETE http://localhost:8080/demo/greeting/ID`

### When run with docker: 

Build docker image: 

* `docker build -t cloudantsample .`
* `docker run -it --rm -p 8080:8080 cloudantsample`

Available endpoints:

* `http://localhost:8080/databases`
* `http://localhost:8080/greeting`
* `http://localhost:8080/greeting/{id}`

Create a new greeting by supplying some content:

`curl -H "Content-Type: application/json" -d '{"content":"test123"}' http://localhost:8080/greeting`

Ask for all known greetings:

`curl http://localhost:8080/greeting`

Ask for a particular greeting:

`curl http://localhost:8080/greeting/ID`

Delete a greeting:

`curl -X DELETE http://localhost:8080/greeting/ID`
