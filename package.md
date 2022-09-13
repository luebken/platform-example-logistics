# Config Package

How to configure, push and publish a configuration.

# Configure

* See [apis/crossplane.yaml]
```
# create repo
up repo create platform-example-logistics

# create package 
up xpkg build --name platform-examples-logistics.xpkg
up xpkg push registry.upbound.io/upbound/platform-example-logistics:v0.0.1

open https://marketplace.upbound.io/configurations/upbound/platform-example-logistics/v0.0.1
```

* build package
* 

How does that relate to orgs / accounts


up repo create test
up xpkg build --name platform-examples-logistics.xpkg


