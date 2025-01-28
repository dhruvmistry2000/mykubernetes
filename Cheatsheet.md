# CheatSheet for Kubernetes
This cheat sheet provides essential kubectl commands for generating YAML templates for various Kubernetes resources. Since it's not possible to remember the complete YAML syntax for all Kubernetes services, these commands help create basic configurations that can be edited according to specific needs. Using these commands with the `--dry-run=client` flag and `-o yaml` output allows you to generate template files that serve as a starting point for your configurations. The generated YAML can then be customized by adding or modifying fields based on your requirements.
The examples below demonstrate common resource types you'll frequently use in Kubernetes deployments.

1) Create a Pods YAML file
```bash
kubectl create pod <pod-name> --image=<image-name> --dry-run=client -o yaml > pod.yaml
```
Example
```bash
kubectl create pod my-pod --image=nginx --dry-run=client -o yaml > pod.yaml
```
2) Create a Services YAML file
```bash
kubectl create service clusterip <service-name> --tcp=<port>:<target-port> --dry-run=client -o yaml > service.yaml
```
Example
```bash
kubectl create service clusterip my-service --tcp=8080:80 --dry-run=client -o yaml > service.yaml
```

3) Create a ConfigMap YAML file
```bash
kubectl create configmap <configmap-name> --from-literal=<key>=<value> --dry-run=client -o yaml > configmap.yaml
```
Example
```bash
kubectl create configmap my-configmap --from-literal=key=value --dry-run=client -o yaml > configmap.yaml
```

4) Create a Secrets YAML file
```bash
kubectl create secret generic <secret-name> --from-literal=<key>=<value> --dry-run=client -o yaml > secret.yaml
```
Example
```bash
kubectl create secret generic my-secret --from-literal=password=secret123 --dry-run=client -o yaml > secret.yaml
```
5) Create a Deployment's YAML file
```bash
kubectl create deployment <deployment-name> --image=<image-name> --replicas=<number-of-replicas> --dry-run=client -o yaml > deployment.yaml
```
Example
```bash
kubectl create deployment my-deployment --image=nginx --replicas=3 --dry-run=client -o yaml > deployment.yaml
```
6) Create a Namespace's YAML file
```bash
kubectl create namespace <namespace-name> --dry-run=client -o yaml > namespace.yaml
```
Example
```bash
kubectl create namespace my-namespace --dry-run=client -o yaml > namespace.yaml
```