# Skaffold

## Install

```bash
brew install skaffold
```

## Getting Started

Start a new terminal and make a temp workdir

```bash
cd "$(mktemp -d)"
```

Clone the Skaffold repo

```bash
git clone 'https://github.com/GoogleContainerTools/skaffold'
cd 'skaffold/examples/buildpacks-node-tutorial'
```

```bash
skaffold init # accept defaults, save
```

```yaml
apiVersion: skaffold/v4beta2
kind: Config
metadata:
  name: buildpacks-node-tutorial
build:
  artifacts:
    - image: skaffold-buildpacks-node
      buildpacks:
        builder: gcr.io/buildpacks/builder:v1
manifests:
  rawYaml:
    - k8s/web.yaml
```

Start Minikube

```bash
minikube start --profile custom
skaffold config set --global local-cluster true
eval "$(minikube -p custom docker-env)"
```

Start Skaffold

```bash
skaffold dev # Ctrl+C to quit
```

### Cleanup

```
minikube delete --all
cd ../../..
rm -rf $PWD
```
