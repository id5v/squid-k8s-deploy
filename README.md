# squid-k8s-deploy


Installing and Configuring Squid for Proxy Testing
Squid is a powerful tool that can be used to test proxy configurations across various libraries. This guide provides step-by-step instructions to set up and configure Squid in a Kubernetes environment. Squid logs can be accessed for review using:

```bash
cat /var/log/squid/access.log
```

## Steps to Install Squid in Kubernetes

1. Deploy Squid using a Kubernetes Deployment
First, deploy Squid using a Kubernetes Deployment, which will create pods running Squid instances.

## Deployment

Apply the Deployment manifest:
```bash
kubectl apply -f squid-deployment.yaml
```
This command creates a Deployment resource that ensures the Squid pods are running. Verify that the Deployment was created successfully:

```bash
kubectl get deployments
```

2. Configure a Service for Squid Access
To allow access to Squid from other pods or external systems, create a Kubernetes 


## Service.

Apply the Service manifest:

```bash
kubectl apply -f squid-service.yaml
```

The Service enables other components to connect to Squid using a dedicated IP address or DNS name. Verify the Service is running:

```bash
kubectl get services
```

## ConfigMap

3. Configure Squid with a ConfigMap
Use a ConfigMap to define Squid's configuration rules and parameters.

Apply the ConfigMap manifest:

```bash
kubectl apply -f squid-config.yaml
```
The ConfigMap stores Squid settings such as allowed IP addresses, ports, and proxying rules. Confirm the ConfigMap has been applied:

```bash
kubectl get configmap
```

## Secrets

4. Set Up Secrets for Squid
If Squid requires sensitive data like authentication credentials, configure Secrets. Create a Secret manifest or use the kubectl create secret command to store this information securely.

```bash
kubectl apply -f squid-secrets.yaml
```

Verify the Secrets are applied:

```bash
kubectl get secrets
```

5. Verify the Deployment
Ensure that the Squid pods are running and functioning correctly:

```bash
kubectl get pods
```
Look for pods with names starting with squid and ensure their status is Running. You can also check the logs for additional debugging:

```bash
kubectl logs -l app=squid
```
