# Kubernetes Golang gRPC demo

This repository contains a simple golang application that demonstrates how to deploy this application to kubernetes.

## Features

  * No need to install protoc compiler because demo using docker-protoc
  * An example of using gRPC Gateway
  * Google APIs included
  * Kubernetes deployment example
  * MySQL data migration example

## Project structure

  * cmd/main.go - main application
  * proto/* - contains a description of application proto files
  * gen/* - contains generated proto files
  * third_party/* - contains third party api's
  * helm/* - helm charts
  * docker-compose.yml - contains a description of gRPC/Protocol buffer compiler containers

## Pre requirements
  * golang 1.16+
  * grpc: `go get google.golang.org/grpc`
  * minikube: `https://minikube.sigs.k8s.io/docs/start`
  * helm: `https://helm.sh`
  * skaffold: `https://skaffold.dev`

## Usage

Compile protobuffs:

```sh
$ make compile-pb
```
or

```sh
$ docker-compose -f docker-compose.yml up
```

Update helm dependencies:

```sh
$ helm dep up ./helm/k8-golang-demo/
```

Start the application:

```sh
$ eval $(minikube docker-env)
$ skaffold dev -p mysql --port-forward=user --no-prune=false --cache-artifacts=false
```
