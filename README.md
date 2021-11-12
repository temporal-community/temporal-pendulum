# Temporal Polyglot Demo - Pendulum

<p align="center">
<img src="img/pendulumnew.png" height="300px" alt="Temporal Pendulum Game"/>
</p>

This demo uses the following Temporal SDKs:

* [Go](https://docs.temporal.io/docs/go/introduction)
* [Java](https://docs.temporal.io/docs/java/introduction)
* [Node](https://docs.temporal.io/docs/node/introduction)
* [PHP](https://docs.temporal.io/docs/php/introduction)

## Running the demo

### Start the Temporal Server

```shell script
git clone https://github.com/temporalio/docker-compose.git
cd docker-compose
docker compose up
```

### Start the positioning services

#### Go Positioning Service

```shell script
cd position-go
go run worker/main.go
```

#### Java Positioning Service

```shell script
cd position-java
mvn compile exec:java -Dexec.mainClass="io.temporal.demo.pendulum.position.Starter"
```

#### Node Positioning Service

If running for the first time:

```shell script
cd position-node
nvm use 16
npm install
npm start
```

For consecutive runs:

```shell script
cd position-node
npm start
```

#### PHP Positioning Service

If running for the first time:

```shell script
cd position-php
composer install
composer update
./rr serve
```

For consecutive runs:

```shell script
cd position-php
./rr serve
```

### Start the game

```shell script
cd game
mvn compile exec:java -Dexec.mainClass="io.temporal.demo.pendulum.Pendulum"
```

### Playing the game

Within the game you can change the positioning implementations
by clicking the buttons on the right.

Notice how the state of the pendulum (position, acceleration, movement)
is preserved once you switch from one workflow to another.
