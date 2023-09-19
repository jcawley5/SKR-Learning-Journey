## Using Services to Create Internal and External Communication with Kubernetes

### STEPS

Depends on Unit-3 exercies

#### Task 1: Create a service manifest and apply it to the cluster

Apply the service manifest to the cluster.

```
kubectl apply -f hello-kyma-svc.yaml
```

Use kubectl to list your services.

```
kubectl get svc
```

Review in the Kyma dashboard under the namespace menu option **Discovery and Network > Services**

#### Task 2: Expose the service with an API Rule

Apply the API Rule manifest to the cluster.

```
kubectl apply -f hello-kyma-api-rule.yaml
```

#### Task 3: View API Rules in the Kyma Dashboard

Open the Kyma Dashboard in your web browser.

Select the API Rules section and choose the hello-kyma API Rule.
