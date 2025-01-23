
# Kubernetes ConfigMaps and Secrets Management
This directory contains Kubernetes configuration files for managing ConfigMaps and Secrets.
1. ConfigMaps store configuration data that is not sensitive, organized as key-value pairs.
2. Secrets are designed to securely store sensitive data, like passwords and tokens, to protect them from unauthorized access.

# Commands to create ConfigMaps and Secrets:
## To create a ConfigMap:
kubectl create configmap <name> --from-literal=<key>=<value>

## Example for creating a ConfigMap:
kubectl create configmap <name> --from-literal=<key1>=<value1> --from-literal=<key2>=<value2> --from-literal=<key3>=<value3>

## To create a Secret from literal values:
kubectl create secret generic <name> --from-literal=<key>=<value>

## Example for creating a Secret:
kubectl create secret generic <name> --from-literal=<key1>=<value1> --from-literal=<key2>=<value2>