# Apply Densify Recommendations to the controller objects

<img src="https://www.densify.com/wp-content/uploads/densify.png" width="300">

The Densify Apply Container Recommendations applies the right-sizing recommendations produced by Densify in a scoped and scheduled process. This is to be used with the Densify Pull-Container-Recommendations app.

- [Requirements](#requirements)
- [Docker Images](#docker-images)
- [Deploy](#deploy)
- [Variables](#Configmap-Annotation_Label-Variables)

## Requirements

* Kubernetes compliant cluster

## Docker images

The Docker images are available on [Docker Hub]
* Apply Recommendations (https://hub.docker.com/r/ssvyper/apply-densify-standard-recommendations)

## Deploy

## Helm

Check out our Helm charts repository: (https://github.com/densify-dev/helm-charts)

## Kustomize (kubectl)

* Configure the (configmap.yml) file with your scoped Densify settings. Connect with your Densify account manager for more details.
* Deploy the files with kubectl (kustomize):
```
kubectl create -k .
```
* Verify that the apply-densify-recommendations pod executed successfully (you may delete it once it has)
* Configure and deploy the scheduled (cronjob.yml) file (you may configure the scheduled frequency; default is once a week):
```
kubectl create -f cronjob.yml
```
