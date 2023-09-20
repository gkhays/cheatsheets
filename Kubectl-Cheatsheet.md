### Namespaces

Show all namespaces.

```console
kubectl --all-namespaces
```

Shorthand

```console
kubectl -A
```

## Logging

```
kubectl --namespace my-namespace get pods
```

```
kubectl logs pod-name
```

```
kubectl logs <pod_name> -n <namespace> --since=12h --timestamps
```

### Tail logs

```
kubectl -f
```

#### Previous logs

```
-p
```

#### Last 20 rows

```
--tail=20
```

## Describe ConfigMap with kubectl

I needed a "one-liner" to determine whether or not the ConfigMap was updated. First, confirm the name of the ConfigMap.

```console
kubectl get configmap -n bridge
NAME                         DATA   AGE
bridge-conf-configmap        1      144d
bridge-init-conf-configmap   1      567d
bridge-jks-configmap         1      144d
kube-root-ca.crt             1      385d
```

Now, describe the settings.

```console
kubectl describe configmaps bridge-conf-configmap -n bridge | grep -C 3 maxQueuedRequests
  idleThreadTimeout: 60s
  maxThreads: 2048
  minThreads: 1024
  maxQueuedRequests: 4096
  requestLog:
    appenders:
      - type: console
```

## References

1. [How to View Kubernetes Pod Logs With Kubectl](https://www.howtogeek.com/devops/how-to-view-kubernetes-pod-logs-with-kubectl/)
2. [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
3. [Viewing a ConfigMap](https://www.aquasec.com/cloud-native-academy/kubernetes-101/kubernetes-configmap/)
