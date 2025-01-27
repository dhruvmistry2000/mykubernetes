# Node Exporter

Node Exporter is a Prometheus exporter that collects and exposes system metrics from *NIX kernels, making them available for monitoring and alerting. It provides detailed hardware and OS metrics like:

- CPU usage and statistics
- Memory usage
- Disk I/O statistics
- Network interface statistics
- Filesystem usage and statistics
- System load
- Many other system metrics

Node Exporter is a fundamental component in modern infrastructure monitoring stacks, especially when used with Prometheus and Grafana for visualization.
To use this configuration, follow these steps to deploy Node Exporter in your Kubernetes cluster. First, apply the configuration file using the command below. This will create the necessary resources for Node Exporter to start collecting system metrics from your cluster nodes.
```bash
kubectl apply -f Node-Exporter/
```

Original Blog:- https://devopscube.com/node-exporter-kubernetes/