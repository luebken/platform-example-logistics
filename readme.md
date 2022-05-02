# Platform Example Logistics

An Example Crossplane Platform for Logistics. 

## Install Providers

```
kubectl crossplane install provider crossplane/provider-aws:v0.26.1

# Create a creds.conf file with the aws cli:
AWS_PROFILE=default && echo -e "[default]\naws_access_key_id = $(aws configure get aws_access_key_id --profile $AWS_PROFILE)\naws_secret_access_key = $(aws configure get aws_secret_access_key --profile $AWS_PROFILE)" > creds.conf

# Create a K8s secret with the AWS creds:
kubectl create secret generic aws-creds -n crossplane-system --from-file=creds=./creds.conf

# Configure AWS Provider by creating a ProviderConfig
cat <<EOF | kubectl apply -f -
apiVersion: aws.crossplane.io/v1beta1
kind: ProviderConfig
metadata:
  name: default
spec:
  credentials:
    source: Secret
    secretRef:
      namespace: crossplane-system
      name: aws-creds
      key: creds
EOF
```

## Platform
Define:
```
kubectl apply -f ship-xrd.yaml
kubectl apply -f ship-dummy-composition.yaml
```

Use:
```
kubectl apply -f ship-1.yaml
```

```
kubectl get ships -o=custom-columns=NAME:.metadata.name,LNG:.status.lng,LAT:.status.lat
```

Delete:
```
kubectl delete ships -f ship-1.yaml
kubectl delete composition.apiextensions.crossplane.io/xships-dummy
kubectl delete compositeresourcedefinition.apiextensions.crossplane.io/xships.logistics.example.com
```

