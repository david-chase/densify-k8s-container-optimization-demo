# Apply Densify Recommendations to VPA

<img src="https://www.densify.com/wp-content/uploads/densify.png" width="300">

The Densify Apply Container Recommendations to VPA app applies the right-sizing recommendations produced by Densify in a scoped and scheduled process. This is to be used with the Densify Pull-Container-Recommendations app.

- [Requirements](#requirements)
- [Docker Images](#docker-images)
- [Deploy](#deploy)
- [Variables](#Configmap-Annotation_Label-Variables)

## Requirements

* Kubernetes or OpenShift
* Vertical Pod Autoscaler (https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler)

## Docker images

The Docker images are available on [Docker Hub]
* Apply Recommendations (https://hub.docker.com/r/ssvyper/apply-densify-vpa-recommendations)

## Deploy

## Kustomize (kubectl)

* Configure the (configmap.yml) file with your scoped Densify and VPA settings. Connect with your Densify account manager for more details.
* Deploy the files with kubectl (kustomize):
```
kubectl create -k .
```
* Verify that the apply-densify-recommendations pod executed successfully (you may delete it once it has)
* Configure and deploy the scheduled (cronjob.yml) file (you may configure the scheduled frequency; default is once a week):
```
kubectl create -f cronjob.yml
```

## Helm

Check out our Helm charts repository: (https://github.com/densify-dev/helm-charts)
