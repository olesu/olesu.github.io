# Minikube

## Getting Started

### Install

```bash
brew install minikube
```

### Start cluster

```bash
minikube start
```

### Use

```bash
alias k='minikube kubectl --'
k get po -A
```

### Example

```bash
k create deployment hello-minikube --image=kicbase/echo-server:1.0
k expose deployment hello-minikube --type=NodePort --port=8080
```

```bash
k get services hello-minikube
```

```bash
minikube service hello-minikube
```

### Clean up

```bash
minikube delete --all
```
