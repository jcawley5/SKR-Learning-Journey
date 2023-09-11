## Working with Kubernetes Workloads

### STEPS: Creating and Testing Serverless Functions

#### Task 1: Create a serverless function via kubectl

Open your terminal and list all current serverless functions in your default namespace:

```
kubectl get functions
```

Create a serverless function using the following command:

```
kubectl apply -n default -f https://raw.githubusercontent.com/kyma-runtime-learning-journey/main/unit_3/functions/hello-world-function.yaml
```

List all current serverless functions again:

```
kubectl get functions
```

View in Kyma Dashboard

### STEPS: Creating and Managing a Deployment

#### Task 1: Create a deployment via the Kyma Dashboard

Open the Kyma Dashboard, navigate to the deployments workload view and choose the Create Deployment button.

- Name: hello-kyma
- Container image: ghcr.io/sap-samples/kyma-runtime-learning-journey/hello-kyma:1.0.0

Choose the YAML tab to review your deployment manifest and choose the Create button and review created resource.

#### Task 2: Update and apply the deployment manifest via kubectl

Use kubectlto list your deployments.

```
kubectl get deployments
```

Enter command, which will create the file hello-kyma-deployoment.yaml with the deployment definition

```
kubectl get deployment hello-kyma -o yaml >> hello-kyma-deployoment.yaml
```

Update the deployment to use a new version of the application. Change the current container image to the new version and set a change-causeto document the change.

- image: ghcr.io/sap-samples/kyma-runtime-learning-journey/hello-kyma:1.0.0
- annotation: kubernetes.io/change-cause: "Upgrade to new release v1.0.1"

Save and apply the updated deployment manifest.

```
kubectl apply -f hello-kyma-deployment.yaml
```

Verify the update in the rollout history or with kubectl describe

```
kubectl rollout history deployment hello-kyma
```

```
kubectl describe deployment hello-kyma
```

#### Task 3: Scale the deployment via kubectl

Scale the deployment to three replicas.

```
kubectl scale deployment hello-kyma --replicas=3
```

Verify it via kubectl.

```
kubectl get deployment hello-kyma
```

#### Task 4: Perform a rollback of the deployment via kubectl

List the rollout history.

```
kubectl rollout history deployment hello-kyma
```

Roll back the deployment by specifying the revision number.

```
kubectl rollout undo deployment hello-kyma --to-revision=1
```

List the rollout history again to verify the rollback.

```
kubectl rollout history deployment hello-kyma
```
