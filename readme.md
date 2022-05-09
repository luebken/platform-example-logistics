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
```

## Install the Logistics Platform
Define:
```
kubectl apply -f ship-xrd.yaml
kubectl apply -f ship-dummy-composition.yaml
```

## Cleanup
```
kubectl delete -f ships.yaml
kubectl delete composition.apiextensions.crossplane.io/xships-dummy
kubectl delete compositeresourcedefinition.apiextensions.crossplane.io/xships.logistics.example.com
```

## Demo

See [demo.md]
