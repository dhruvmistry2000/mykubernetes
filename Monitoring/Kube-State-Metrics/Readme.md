# Kube-state-metrics
Kube-state-metrics is a service that listens to the Kubernetes API and generates metrics about the state of the objects in the cluster. It provides insights into the health and performance of Kubernetes resources, such as deployments, pods, and nodes. Unlike traditional metrics that focus on resource usage (like CPU and memory), kube-state-metrics focuses on the state of the Kubernetes objects, allowing users to monitor the status and health of their applications and infrastructure.By using kube-state-metrics, teams can gain a deeper understanding of their Kubernetes clusters, enabling them to troubleshoot issues, optimize resource usage, and maintain the overall health of their applications.

To use this configuration, follow these steps to deploy kube-state-metrics in your Kubernetes cluster. First, apply the configuration file using the command below. This will create the necessary resources for kube-state-metrics to start collecting metrics about the state of your Kubernetes objects.
```bash
kubectl apply -f Kube-State-Metrics/
```

Original Blogs:- https://devopscube.com/setup-kube-state-metrics/