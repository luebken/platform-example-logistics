# Platform Example Logistics

An Example Crossplane Platform for Logistics. 

## Install K8s & Crossplane
```
kind create cluster --image kindest/node:v1.23.5
helm install crossplane --namespace crossplane-system --create-namespace crossplane-stable/crossplane
```

## Install Providers
```
kubectl crossplane install provider luebken/provider-gps-dummy:v0.1.4
kubectl crossplane install provider crossplane/provider-nop:v0.1.1
kubectl apply -f config-provider-gps.yaml
```

## Install the Logistics Platform
```
kubectl apply -f ship-xrd.yaml
kubectl apply -f ship-dummy-composition.yaml
kubectl apply -f truck-xrd.yaml
kubectl apply -f truck-dummy-composition.yaml

kubectl get xrds
kubectl get compositions
```
## Install Example Data

```
kubectl apply -f ships.yaml
kubectl apply -f trucks.yaml
```

## Cleanup
```
kubectl delete -f ships.yaml
kubectl delete composition.apiextensions.crossplane.io/xships-dummy
kubectl delete compositeresourcedefinition.apiextensions.crossplane.io/xships.logistics.example.com
```

## Demo

See [demo.md]
