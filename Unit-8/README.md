## Performing Observability and Monitoring

### Task 1

Create a new namespace called monitoring-exercise:

```
kubectl create namespace monitoring-exercise
```

Create a new deployment called hello-kyma in the monitoring-exercise namespace:

```
kubectl apply -n monitoring-exercise -f https://raw.githubusercontent.com/SAP-samples/kyma-runtime-learning-journey/main/unit_8/hello-kyma-deployment-svc.yaml
```

Verify the successful creation of the deployment:

```
kubectl get deployments -n monitoring-exercise
```

Port-forward the hello-kyma service to your local machine:

Leave this terminal window open and open http://localhost:8080/metrics in a new browser tab. You should see a lot of metrics being exposed by the hello-kyma application.

```
kubectl port-forward -n monitoring-exercise svc/hello-kyma 8080:8080
```

### Task 2

Create a new namespace called monitoring-exercise:

```
kubectl create namespace monitoring-exercise
```

Create a new deployment called hello-kyma in the monitoring-exercise namespace:

```
kubectl apply -n monitoring-exercise -f https://raw.githubusercontent.com/SAP-samples/kyma-runtime-learning-journey/main/unit_8/hello-kyma-deployment-svc.yaml
```

Verify the successful creation of the deployment:

```
kubectl get deployments -n monitoring-exercise
```

Port-forward the hello-kyma service to your local machine:

```
kubectl port-forward -n monitoring-exercise svc/hello-kyma 8080:8080
```

Configure Prometheus to scrape the metrics endpoint and use Prometheus UI to query the metrics.

Apply the ServiceMonitor resource to the kyma-system namespace:

```
kubectl apply -n kyma-system -f hello-kyma-servicemonitor.yaml
```

Verify that the ServiceMonitor resource was created successfully:

```
kubectl get servicemonitors -n kyma-system
```

Verify that Prometheus is scraping the metrics endpoint of the hello-kyma service:
Open the Prometheus UI by running the following command:

```
kubectl port-forward -n kyma-system svc/monitoring-prometheus 9090:9090
```

Open http://localhost:9090/targets in a new browser tab. You should see serviceMonitor/kyma-system/monitoring-hello-kyma listed as a target.
Open http://localhost:9090/graph and enter the following query

This query will return the number of successful requests to the hello-kyma service. You should see a graph for the last 5 minutes.

```
promhttp_metric_handler_requests_total{service="hello-kyma", code="200"}
```

### Task 3

Open the Grafana UI by running the following command:

```
kubectl port-forward -n kyma-system svc/monitoring-grafana 3000:80
```

Open http://localhost:3000 in a new browser tab.

On the left side, click the Explore button.

In the Explore view, click the Add Query button.

In the Query field, enter the following query:

```
rate(promhttp_metric_handler_requests_total{service="hello-kyma", code="200"}[1m])
```

This query will return the number of successful requests to the hello-kyma service per minute.
