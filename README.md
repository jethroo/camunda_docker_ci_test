[![CI](https://github.com/jethroo/camunda_docker_ci_test/actions/workflows/ci.yml/badge.svg)](https://github.com/jethroo/camunda_docker_ci_test/actions/workflows/ci.yml)

# Example for testing business process models (BPMN) in Camunda via github actions

This repo shows an example setup for github actions to develop and run business process models with camunda.


## Example BPMN

The showcase uses a relatively simple example for now, but it should provide enough insight to tackle more complex scenarios later on. 

![Bildschirmfoto 2025-05-28 um 16 24 15](https://github.com/user-attachments/assets/98cd79da-2694-44ff-8e48-b76f73be33d7)


## Linting

BPMN lint is running as part of the github actions.

## Tests

Prerecorded tests, bundled as a Postman collection, are run via the Newman CLI ([newman](https://www.npmjs.com/package/newman)) against a dockerized [Camunda](https://camunda.com) instance within GitHub Actions.

The collection contains following steps
* ping the camunda app 
* deploy a [business process model](camundor.bpmn)
* start a process via process definition key
* check for waiting external task
* fetch and lock of said external task 
* complete the external task
* delete the process model deployment

```bash
┌─────────────────────────┬──────────────────┬──────────────────┐
│                         │         executed │           failed │
├─────────────────────────┼──────────────────┼──────────────────┤
│              iterations │                1 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│                requests │                7 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│            test-scripts │                7 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│      prerequest-scripts │                0 │                0 │
├─────────────────────────┼──────────────────┼──────────────────┤
│              assertions │                8 │                0 │
├─────────────────────────┴──────────────────┴──────────────────┤
│ total run duration: 18.4s                                     │
├───────────────────────────────────────────────────────────────┤
│ total data received: 6.67kB (approx)                          │
├───────────────────────────────────────────────────────────────┤
│ average response time: 2.6s [min: 28ms, max: 17.5s, s.d.: 6s] │
└───────────────────────────────────────────────────────────────┘
```
