# Apply Densify Annotations

<img src="https://www.densify.com/wp-content/uploads/densify.png" width="300">

The Densify Apply-Annotations app applies the right-sizing recommendations produced by Densify in a scoped and scheduled process. This is to be used with the Densify Pull-Container-Recommendations app.

- [Requirements](#requirements)
- [Docker Images](#docker-images)
- [Deploy](#deploy)
- [License](#license)

## Requirements

* Kubernetes or OpenShift

## Docker images

The Docker images are available on [Docker Hub]
* Apply Annotations (https://hub.docker.com/r/ssvyper/apply-densify-annotations)

## Deploy

## Helm

Check out our Helm charts repository: (https://github.com/densify-dev/helm-charts)

## Kustomize (kubectl)

* Configure the (configmap.yml) file with your scoped Densify and annotation settings. Connect with your Densify account manager for more details.
* Deploy the files with kubectl (kustomize):
```
kubectl create -k .
```
* Verify that the apply-densify-annotations pod executed successfully (you may delete it once it has)
* Configure and deploy the scheduled (cronjob.yml) file (you may configure the scheduled frequency; default is once a week):
```
kubectl create -f cronjob.yml
```

# Configmap Annotation/Label Variables

The following variables can be used for the annotation/label.

| Variable | Description|
| -------- | -----------|
| {namespace} | Namespace |
| {podName} | Pod Name |
| {containerName}  | Container Name |
| {recommendationType} | Recommendation Type, ex. Downsize, Upsize, Resize, Size from Unspecified |
| {containerCurCPUReq} | Container Current CPU Request |
| {containerCurCPULim} | Container Current CPU Limit |
| {containerCurMemReq} | Container Current Memory Request |
| {containerCurMemLim} | Container Current Memory Limit |
| {containerRecCPUReq} | Container Recommended CPU Request |
| {containerRecCPULim} | Container Recommended CPU Limit |
| {containerRecMemReq} | Container Recommended Memory Request |
| {containerRecMemLim} | Container Recommended Memory Limit |
| {curDate} | Current Date |
| {curTime} | Current Time |

Note: If a pod has multiple containers, the container with the largest current & recommended CPU/Memory request values will be selected. This is to avoid small "sidecar" container recommendations. These can also be removed/filtered out in the Filters section of the configmap.

# License

Apache 2 Licensed. See [LICENSE](../../LICENSE) for full details.
