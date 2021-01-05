# Telemetry Reactor Specification

Telemetry Reactor for Node is an implementation of the treactor-specification. It is part of a set of microservices designed for learning, testing, and experimenting with the concepts of observability.

Telemetry Reactor (or TReactor for short) is a set of microservices designed to learn, test and experiment 
with observability of microservices. You should be able to play with it on your own machine in `local`, 
but it gets interesting when you deploy it in a Kubernetes cluster.

It gets interesting when deployed in a cluster, where you can have up to a bit over 120 microservices 
(atoms in the mendeleev table). Controlling the microservices is done by create telemetry reactions
(treactions) on a `molecules`. This will create cascading calls throughout the treactor. The calls and
events can be observed into the observability platform of your choice.

## Implementations

This GitHub organisation includes a set of opinionated [implementations](implementations.md) of this 
spec. The opinions include:

* Observability framework based on [OpenTelemetry](https://opentelemetry.io/).
* Clustering and orchestration based on [Kubernates](https://kubernetes.io/).
* Optional service mesh based on [Istio](https://istio.io/).
* Eventing based on [CloudEvents](https://cloudevents.io/) and [KNative](https://knative.dev/) (Future).

The options are, just opinions. Anyone can implement this spec to create a tool to demonstrate an 
other framework (be it other observability framework, orchestration technology, mesh, etc...). Read
the implementation [HOWTO](implement-howto.md) for step-by-step instructions.

## Example

To see what treactor does lets take a very simple example. TReactor works by splitting molecules:

`[[H]]^2[O]`

Everything between the brackets `[]` will be a call to the next microservice. The brackets can be prefixed with a number
and an optional parameter (`s` or `p`), this tells treactor how many times the service needs to be called and how (
sequential or parallel). Multiple calls can be make by appending them using `^` (sequential) or `*` (parallel).

Depending on the content of the bracket the call will be different. If treactor detects an atom a call to the corresponding
atom service will be made. But if treactor detects another sub-molecule it calls the next bond and apply the same
logic till only atoms are left. So the example above will result in:

`http://treactor-api/treact/split?molecule=[[H]]^2[O]`

calling

* `http://bond-1/treact/split?molecule=[h]`
* `http://atom-o/treact/atom?symbol=o`
* `http://atom-o/treact/atom?symbol=o`

*bond* will split the molecule [H] (ok, this looks strange, but each bracket is a layer) into it's atoms, in this
case only 1 `H`:

* `http://atom-h/treact/atom?symbol=H`

Try the local [installation](installation.md), to see how it looks in the trace (this will make it more clear).

## Specification

[Specification](specification.md)

## Scenarios

[Scenarios](scenarios/README.md)