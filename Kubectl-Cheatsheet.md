Logging

```
kubectl --namespace my-namespace get pods
```

```
kubectl logs pod-name
```

```
kubectl logs <pod_name> -n <namespace> --since=12h --timestamps
```

Tail logs
```
kubectl -f
```

Previous logs
```
-p
```

Last 20 rows
```
--tail=20
```


##References

1. [How to View Kubernetes Pod Logs With Kubectl](https://www.howtogeek.com/devops/how-to-view-kubernetes-pod-logs-with-kubectl/)
2. [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
