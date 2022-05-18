# Platform Example Logistics

An Example Crossplane Platform for Logistics. 

## Install K8s & Crossplane
```
kind create cluster --image kindest/node:v1.23.5
helm install crossplane --namespace crossplane-system --create-namespace crossplane-stable/crossplane

kubectl get pods -n crossplane-system
helm list -n crossplane-system
kubectl get crds
```

## Install Providers
```
kubectl crossplane install provider crossplane/provider-nop:v0.1.1
kubectl crossplane install provider luebken/provider-gps-dummy:v0.1.7
kubectl apply -f config-provider-gps.yaml

kubectl get providers
```

## Cleanup
```
kubectl delete -f examples/
kubectl delete -f apis/

kind delete clusters kind
```

## Demo

See [demo.md]
