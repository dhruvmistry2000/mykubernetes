# Prometheus
Prometheus is an open-source monitoring and alerting toolkit designed for reliability and scalability. It is particularly well-suited for monitoring dynamic cloud-native environments, such as those orchestrated by Kubernetes. Prometheus collects metrics from configured targets at specified intervals, stores them in a time-series database, and provides a powerful query language (PromQL) for retrieving and manipulating the data.
Prometheus is widely adopted in the Kubernetes ecosystem and is a key component for monitoring applications and infrastructure in cloud-native environments.
 # Setting up Prometheus
 To set up Prometheus in your Kubernetes cluster, follow these steps:

 1. **Create a Cluster Role**: This role defines the permissions for Prometheus to access the necessary resources in the cluster. Run the following command:
 ```bash
 kubectl create -f clusterRole.yaml
 ```

 2. **Create a ConfigMap**: The ConfigMap holds configuration data that Prometheus will use to scrape metrics from your applications. Execute this command:
 ```bash
 kubectl create -f config-map.yaml
 ```

 3. **Create a Prometheus Deployment**: This step deploys the Prometheus server, which will run in your cluster and collect metrics. Use the command:
 ```bash
 kubectl create -f prometheus-deployment.yaml 
 ```

 4. **Check the Deployment**: After deploying, verify that the Prometheus deployment is running correctly by listing the deployments in the monitoring namespace:
 ```bash
 kubectl get deployments --namespace=monitoring
 ```

 5. **Create a Service**: Finally, expose the Prometheus service to allow access from outside the cluster. This command will create the service:
 ```bash
 kubectl create -f prometheus-service.yaml --namespace=monitoring
 ```

 This setup will expose the Prometheus service on port 30000, allowing you to access the Prometheus UI and metrics.

 Original Blogs:-  https://devopscube.com/setup-prometheus-monitoring-on-kubernetes/