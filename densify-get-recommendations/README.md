# Pull Densify Recommendations

<img src="https://www.densify.com/wp-content/uploads/densify.png" width="300">

The Densify Pull-Container-Recommendations app pulls the Densify container right-sizing recommendations and stores it for later use. This is to be used with the Densify Apply-Container-Recommendations app.

- [Requirements](#requirements)
- [Docker Images](#docker-images)
- [Deploy](#deploy)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Requirements

* Densify instance details
* Cluster name (specified in Densify)
* Kubernetes or OpenShift
* Persistent storage (default storage class; ~20MB)

## Docker images

The Docker images are available on [Docker Hub]
* Pull Recommendations (https://hub.docker.com/r/ssvyper/pull-densify-recommendations)

## Deploy

## Helm

Check out our Helm charts repository: (https://github.com/densify-dev/helm-charts)

## Kustomize (kubectl)

* Configure the (configmap.yml) file with your Densify Connection and k8s Cluster settings
```
kubectl create secret generic densify-instance-auth -n densify --from-literal=user=USERNAME --from-literal=pass=PASSWORD
```
* Deploy the files with kubectl (kustomize):
```
kubectl create -k .
```
* Verify that the pull-densify-recommendations pod executed successfully (you may delete it once it has)
* Deploy the scheduled (cronjob.yml) file (you may configure the scheduled frequency; default is once a day):
```
kubectl create -f cronjob.yml
```

## Troubleshooting

Check that the Persistent Volume Claim was able to successfully bound to a storage volume.
Check the pod logs for errors.

## License

Apache 2 Licensed. See [LICENSE](../../LICENSE) for full details.
