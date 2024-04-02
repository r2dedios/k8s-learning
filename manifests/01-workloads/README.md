# K8s Workloads

Before starting, run the following commands to prepare our environment for our
examples.
```sh
kubectl create ns k8s-workloads
kubectl config set-context --current --namespace=k8s-workloads
```
## Deployments
A Deployment provides declarative updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller
changes the actual state to the desired state at a controlled rate. You can
define Deployments to create new ReplicaSets, or to remove existing Deployments
and adopt all their resources with new Deployments.

:warning: **Do not manage ReplicaSets owned by a Deployment. Consider opening an issue
in the main Kubernetes repository if your use case is not covered below.**

* [K8S Deployments Doc](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
* [OCP Deployments Doc](https://docs.openshift.com/container-platform/4.14/applications/deployments/what-deployments-are.html)

:blue_book: Commands:
```sh
kubectl apply -f ./deployment.yaml
kubectl describe deployments nginx-deployment
```

## ReplicaSets
A ReplicaSet's purpose is to maintain a stable set of replica Pods running at
any given time. As such, it is often used to guarantee the availability of a
specified number of identical Pods.

## StatefulSets
StatefulSet is the workload API object used to manage stateful applications.

Manages the deployment and scaling of a set of Pods, and provides guarantees
about the ordering and uniqueness of these Pods.

Like a Deployment, a StatefulSet manages Pods that are based on an identical
container spec. Unlike a Deployment, a StatefulSet maintains a sticky identity
for each of its Pods. These pods are created from the same spec, but are not
interchangeable: each has a persistent identifier that it maintains across any
rescheduling.

If you want to use storage volumes to provide persistence for your workload, you
can use a StatefulSet as part of the solution. Although individual Pods in a
StatefulSet are susceptible to failure, the persistent Pod identifiers make it
easier to match existing volumes to the new Pods that replace any that have
failed.

* [K8S Deployments Doc](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)
* [OCP Deployments Doc](https://docs.openshift.com/container-platform/4.14/rest_api/workloads_apis/statefulset-apps-v1.html)

:blue_book: Commands:
```sh
# Prepare Storage. By default, K8s doesn't have any storage provider, and needs
to be configured manually
kubectl apply -f ./storage-setup.yaml

# deploy app
kubectl apply -f ./statefulset.yaml
kubectl describe statefulset nginx-stateful
```

## DaemonSets

## Jobs

## CronJobs

## DeploymentConfigs
> :heavy_exclamation_mark: **As of OpenShift Container Platform 4.14,
> DeploymentConfig objects are deprecated. DeploymentConfig objects are still
> supported, but are not recommended for new installations. Only security-related
> and critical issues will be fixed. Instead, use Deployment objects or another
> alternative to provide declarative updates for pods.**

* [OCP Deployments Doc](https://docs.openshift.com/container-platform/4.14/applications/deployments/what-deployments-are.html#deployments-and-deploymentconfigs_what-deployments-are)
