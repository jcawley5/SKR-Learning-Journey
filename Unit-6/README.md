## Using Kyma Eventing

### STEPS

#### Task 1: Set up a new namespace

Within the Kyma dashbaord create the namespace `eventing`

In the `eventing` namespace navigate to `Workloads / Functions` and select Create Function: create a `nodejs` function named `lastorder` with code

```
console.log("Received event:", event.data);
```

Navigate to ` workloads / functions`` and select the menu  `Configuration`. Here, choose `Create Subscription` and create a subscription with…

- Name: lastorder-sub
- Service lastorder
- Filter 1: sap.kyma.custom.myapp.order.received.v1
- Filter 2: sap.kyma.custom.myapp.order.changed.v1

Trigger the workload with an event.

Open a terminal window and run:

```
kubectl -n kyma-system port-forward service/eventing-event-publisher-proxy 3000:80
```

Open another terminal window and run the following in order to publish the event order.received.v1 and trigger the function:

```
curl -v -X POST -H "ce-specversion: 1.0" -H "ce-type: sap.kyma.custom.myapp.order.received.v1" -H "ce-source: myapp" -H "ce-eventtypeversion: v1" -H "ce-id: cc99dcdd-6f6d-43d6-afef-d024eb276584" -H "content-type: application/json" -d "{\"orderCode\":\"3211213\", \"orderStatus\":\"received\"}" http://localhost:3000/publish
```

```
curl -v -X POST -H "ce-specversion: 1.0" -H "ce-type: sap.kyma.custom.myapp.order.changed.v1" -H "ce-source: myapp -H "ce-eventtypeversion: v1" -H "ce-id: 94064655-7e9e-4795-97a3-81bfd497aac6" -H "content-type: application/json" -d "{\"orderCode\":\"3211213\", \"orderStatus\":\"changed\"}" http://localhost:3000/publish
```

Confirm by reviewing function’s logs
