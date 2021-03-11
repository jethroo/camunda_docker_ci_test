# camunda_docker_ci_test

This repo shows an example setup for github actions.

## Linting

BPMN lint is running as part of the github actions.

## Tests

Postman tests ([newman](https://www.npmjs.com/package/newman)) are run against a dockerized [Camunda](https://camunda.com) instance via github actions.
