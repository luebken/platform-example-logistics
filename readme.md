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

Use:
```
kubectl apply -f ship-1.yaml

kubectl get ships -o=custom-columns=NAME:.metadata.name,LNG:.status.lng,LAT:.status.lat
NAME            LNG       LAT
ship-test-123   1.35469   53.99429
```

Cleanup:
```
kubectl delete -f ship-1.yaml
kubectl delete composition.apiextensions.crossplane.io/xships-dummy
kubectl delete compositeresourcedefinition.apiextensions.crossplane.io/xships.logistics.example.com
```