## Using Kubernetes Storage and StatefulSets

Apply the file to the cluster:

```
kubectl apply -f pv.yaml
```

Check if the PersistentVolume was created:

```
kubectl get pv my-persistent-volume
```

Apply the file to the cluster:

```
kubectl apply -f pvc.yaml
```

Check if the PersistentVolumeClaim was created:

```
kubectl get pvc postgres-claim
```

Apply the file to create the StatefulSet.

```
kubectl apply -f postgres.yaml
```

Check if the StatefulSet was created.

```
kubectl get statefulset postgres
```

Check if the Pod postgres-0 was created.

```
kubectl get pod postgres-0
```

Verify that the PersistentVolumeClaim is bound.

```
kubectl get pvc postgres-claim
```

You can also play around with the postgres database. You can connect to it locally by port-forwarding the postgres-0 Pod to your local machine.

```
kubectl port-forward postgres-0 5432:5432
```
