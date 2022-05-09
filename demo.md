# Demo

The following demo shows how Crossplane and the Kubernetes ecosystem can be used to build digital twins in the logistics field.

A digital twin is a unique digital representation that serves as the real-time digital counterpart of a physical object or process. It updates itself on it's state, condition and context. And provider value by visualization, analysis, prediction and optimization.

We will be demoing the following: 

1. How to compose Digital Twins with XRDs
2. How to query Digital Twins
3. How to enrich Digital Twins with Custom Sensors
4. How to enrich Digital Twins with Cloud Resources
5. How Digital Twins are updateting themselves
6. How to update Digital Twins
7. How to move Digital Twins
8. K8s tools

## 1. Composing Digital Twins
* Explain XRD:
  * cat ship-xrd.yaml
  * cat truck-xrd.yaml

## 2. Query
```
kubectl get ships
kubectl get trucks
kubectl get trucks -l ship=petunia-seaways
```

## 3. Enrich with Custom Senors
* Explain Providers
  * Walk through dummy GPS provider: https://github.com/luebken/provider-gps-dummy
  * TBD: Walk through MQTT powered fuel provider

* Explain Compositions
  * cat ship-dummy-composition.yaml

TODO query ships in a specific region (with some geo spatial api)
TODO Open Google Maps

## 4. Enrich with Cloud Resources
TODO. Add some simple S3 bucket to store some data

## 5. Reconciliation
* Recap on desired state vs actual state
* TODO find a good drift example
* TODO show how a sensor change propagates to the XRD 

## 6. Change XRDs
* Update the XRD for a vessel to be on another ship
* Note that this could also be a service in the future. Self drving trucks.

## 7. Move XRDs
* Bacup and deploy with velero

## 8. K8s Tools
TODO use other tooling from the K8s ecosystem e.g. Lens, Velero, Prometheus, Loki, Traffic, LinkerD, Robusta, Datree, Kverno

