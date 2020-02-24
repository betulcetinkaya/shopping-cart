# Project Title

Shopping Cart

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

```
Docker
```

### Installing
You need to clone the repositories with submodules included.

```
git clone --recursive https://github.com/betulcetinkaya/trendyol-case.git
```

## Running the tests
Before running the tests you need to run assignment-db for repository tests (See deployment for notes on how to deploy a module). You need to move into the base package of the submodules(repositories) and then you can run the following command.

```
mvn clean test
```

## Deployment

To run all the services and platforms apply the following steps.

1. Move into "docker-deployment" folder.
2. Run "docker-compose up -d" command

To run a single service
1. Move into src/main/resources/docker folder of a specific submodule (repository).
2. Run "docker-compose up -d" command

## Built With

* [Jdk11]
* [Docker]
* [Maven]
* [Spring]

## Authors

* **Betül Çetinkaya** - *Initial work* - (https://github.com/betulcetinkaya)
