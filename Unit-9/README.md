## Unit-9 Exercise STEPS

### STEPS

- Create a new namespace called service-management in the Kyma dashboard
- Create a Service Instance using the Kyma Dashboard by navigating to Service Management → Service Instances and select Create Service Instance:
  - name: credential-store
  - offering name: credstore
  - plan name: free
- Check the Service Instance on the SAP BTP Cockpit
  - Navigate to your SAP BTP Cockpit.
  - Go to Services / Instances and Subscriptions.
  - Check if the instance `credential-store` displays in the list of instances. If it isn't, navigate back to your Kyma Dashboard to double check that the status of your set up service instance states provisioned:
- Create a Service Binding using the Kyma Dashboard which will automatically create a Kubernetes secret with the binding metadata and credentials
- Your Kyma Dashboard will now show your set up Service Instance credential-store. On this overview page, click `Create BTP Service Binding` to set up a Service Binding:
  - name: credstore-binding
  - Service Instance Name: credential-store
- Check the Service Binding on the SAP BTP Cockpit
  - Navigate to your SAP BTP Cockpit and then go to Services / Instances and Subscriptions.
  - Choose the arrow of your set up instance credential-store. Then you will see your newly created Service Binding credstore-binding:

Congratulations! You have successfully completed this exercise about Service Management on the SAP BTP, Kyma runtime. You were able to create a Service Instance as well as a Service Binding on the Kyma Dashboard and verify them both on the SAP BTP Cockpit.
