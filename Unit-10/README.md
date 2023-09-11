## Using ConfigMaps and Secrets

### STEPS

#### Task 1: Create a ConfigMap

Apply the ConfigMap via kubectl.

```
kubectl apply -f config-map.yaml
```

Check if the ConfigMap has been created:

```
kubectl get configmaps
```

#### Task 2: Deploy an application with the ConfigMap and verify the result

Apply the deployment via kubectl.

```
kubectl apply -f deployment.yaml
```

Get the pod name.

```
kubectl get pods -l app=test-configmap
```

Get the output of the pod.

```
kubectl logs <pod-name>
```

Alternatively, you could also retrieve the logs via the label selector:

```
kubectl logs -l app=test-configmap
```

Delete the deployment

```
kubectl delete deployment test-configmap
```
