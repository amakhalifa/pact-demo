# Pact demo

Simple example project that uses pacts with Java.

There are 2 sub projects:
1. provider - A rest service with a hello world endpoint.
2. consumer - A consumer of the hello world endpoint

With this project you will be able to
1. Create a pact using the consumer
2. Publish it to a pact broker
3. Verify that the provider fulfills the pact


## Steps

### Start the provider service
```sh
gradlew clean build && java -jar provider/build/libs/gs-actuator-service-0.1.0.jar
```

### Start a pact broker

```sh
cd pact-broker
docker-compose up
```

### Publish a pact

To create a pact in the consumer/build/pacts run:

```sh
gradlew :consumer:test
```

publish the pact:

```sh
gradlew :consumer:pactPublish
```

### Verify the pact

```sh
gradlew -Ppact.verifier.publishResults=true :provider:pactVerify
```