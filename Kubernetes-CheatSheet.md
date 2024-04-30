# Kubernetes Cheat Sheet

### Set and use context

```console
kubectl config set-context --current --namespace applications
kubectl config use-context $EKS_CLUSTER_ARN
```

I mostly use [kubectx](https://github.com/ahmetb/kubectx) but it is helpful to know how to do it in `kubectl`.

### Get deployments

```console
kubectl get deployments.v1.apps -o json -n test
```

### Get pods

```console
kubectl get pods -o wide -n test
```

Pods that are running.

```console
kuubectl get pods -n test --field-selector=status.phase==Running
```

### Describe pods

```console
kubectl describe pods/bridge-client-876b58b4d-tsbhc -n test
```

### Shell into a pod

```console
kubectl exec -it --namespace=tools mongo-pod -- bash -c "mongo"
```

Double dash separates the kubectl arguments from what is to be run inside the pod.

### Get component status

```console
kubectl get componentstatuses -n test
```

### Get events

```console
kubectl -n test get events
```

### View logs

```console
kubectl logs bridge-client-6df4b7bfdc-2trr5 -n test
kubectl logs bridge-client-6df4b7bfdc-2trr5 -n test -f
```

### Get the pod disruption budget

```console
kubectl get poddisruptionbudget
```

## References

1. [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
2. [Kubernetes (kubectl) get running pods](https://stackoverflow.com/a/58531936/6146580)
