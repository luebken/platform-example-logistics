# Platform Example Logistics

An Example Crossplane Platform for Logistics. 

## Install K8s & UXP

Note: I'm doing this here with [Universal-Crossplane](https://github.com/upbound/universal-crossplane) but this could also be done with any other Crossplane distribution.

```
# install the up CLI
curl -sL https://cli.upbound.io | sh

# create a kind cluster
kind create cluster --image kindest/node:v1.24.3

# install UXP
up uxp install

helm install crossplane --namespace crossplane-system --create-namespace crossplane-stable/crossplane
kubectl get pods -n upbound-system
helm list -n upbound-system
kubectl get crds
```

## Install Providers
```
kubectl crossplane install provider crossplane/provider-nop:v0.1.1
kubectl crossplane install provider luebken/provider-gps-dummy:v0.1.7
kubectl get providers

kubectl apply -f config-provider-gps.yaml
kubectl get secrets -n upbound-system
kubectl get providerconfigs.gps.crossplane.io
```

## Cleanup
```
# Delete 
kubectl delete -f examples/
kubectl delete -f apis/

kind delete clusters kind
```

## Demo

See [demo.md](demo.md)
