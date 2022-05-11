# Platform Example Logistics

An Example Crossplane Platform for Logistics. 

## Install K8s & Crossplane
```
kind create cluster --image kindest/node:v1.23.5
helm install crossplane --namespace crossplane-system --create-namespace crossplane-stable/crossplane

kubectl get pods -n crossplane-system
helm list -n crossplane-system
```

## Install Providers
```
kubectl crossplane install provider crossplane/provider-nop:v0.1.1
kubectl crossplane install provider luebken/provider-gps-dummy:v0.1.4
kubectl apply -f config-provider-gps.yaml
```

## Install the Logistics Platform
```
kubectl apply -f apis/

kubectl get xrds
kubectl get compositions
```
## Install Example Data

```
kubectl apply -f examples/

kubectl get terminals,ships,trucks,containers
```

## Cleanup
```
kubectl delete -f examples/
kubectl delete -f apis/
```

## Demo

See [demo.md]
