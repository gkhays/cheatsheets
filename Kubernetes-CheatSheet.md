# Kubernetes Cheat Sheet

### Set and use context

```console
kubectl config set-context --current --namespace applications
kubectl config use-context $EKS_CLUSTER_ARN
```

I mostly use [kubectx](https://github.com/ahmetb/kubectx) but it is helpful to know how to do it in `kubectl`.

### Get deployments

```console
kubectl get deployments.v1.apps -o json -n bridge
```

### Get pods

```console
kubectl get pods -o wide -n bridge
```

### Describe pods

```console
kubectl describe pods/bridge-client-876b58b4d-tsbhc -n bridge
```

### Get component status

```console
kubectl get componentstatuses -n bridge
```

### Get events

```console
kubectl -n bridge get events
```

### View logs

```console
kubectl logs bridge-client-6df4b7bfdc-2trr5 -n bridge
kubectl logs bridge-client-6df4b7bfdc-2trr5 -n bridge -f
```

### Get the pod disruption budget

```console
kubectl get poddisruptionbudget
```

## References

1. [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
