## Discovering Kubernetes

### STEPS

> The kubeconfig can be found on the BTP Cockpit on the **Overview** menu option under **Kyma Environment**

- https://kubernetes.io/docs/tasks/tools/install-kubectl
- https://github.com/int128/kubelogin
- Set env variable
  - Linux/MAC: export KUBECONFIG=<KUBECONFIG_FILE_PATH>
  - Windows Powershell: $ENV:KUBECONFIG="<KUBECONFIG_FILE_PATH>"
  - Windows DOS: set KUBECONFIG="<KUBECONFIG_FILE_PATH>"

#### Interacting with the Kubernetes API via Kubectl

```
kubectl get pods
```

```
kubectl get pods --namespace my-namespace
```

```
kubectl get services
```

```
kubectl get replicasets
```

```
kubectl get deployments
```

```
kubectl create -f my-pod.yaml
```

```
kubectl create -f https://raw.githubusercontent.com/SAP-samples/kyma-runtime-learning-journey/main/unit_1/my-pod.yaml
```

```
kubectl apply -f my-pod.yaml
```

```
kubectl describe pod my-pod
```

```
kubectl describe pod my-pod -o yaml > my-pod.yaml
```

```
kubectl label pod my-pod my-label=my-value
```

```
kubectl delete pod my-pod
```
