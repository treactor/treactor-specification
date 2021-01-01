## Installation

### Pre-Requirement

Create a directory `tmp` and `work` in this repo. Don't worry, they are in the `.gitignore` so you do not accidentally
check them in.

### Local

Build the `treactor` from source

`go install ./cmd/treactor/`

Set the environmental variables. Replace `project-name` project with your own

```
export PORT=3330
export TREACTOR_NAME=reactor-api
export TREACTOR_VERSION=1
export TREACTOR_DEBUG=1
export TREACTOR_PROFILE=0
export TREACTOR_MODE=local
```

Fire up the treactor

`treactor`

And test it by calling:

http://localhost:3330/treact/split?molecule=[[H]]^2[O]

Go to the Cloud Console, select *Trace*.

### Kubernetes

*Not yet fully tested/supported*


`go install ./cmd/trprep/`

`kubectl label namespace default istio-injection=disabled --overwrite`

### Istio

*Not yet fully tested/supported*

`kubectl label namespace default istio-injection=enabled --overwrite`
