# Taints and Tolerations in Kubernetes
Taints and tolerations are mechanisms in Kubernetes that allow nodes to repel (taint) or accept (tolerate) certain pods based on specific conditions. They help ensure that pods are scheduled only on appropriate nodes, improving scheduling flexibility.

1. Taints are applied to nodes and allow nodes to repel certain pods unless those pods have matching tolerations. There are three main types of taints:
   - **NoSchedule**: Pods that do not tolerate the taint will not be scheduled on the node.
   - **PreferNoSchedule**: Kubernetes will try to avoid scheduling pods that do not tolerate the taint on the node, but it is not guaranteed.
   - **NoExecute**: Pods that do not tolerate the taint will be evicted from the node if they are already running there.
2. Tolerations are applied to pods and allow them to be scheduled on nodes with specific taints.

To apply taint on a node:
```bash
kubectl taint nodes <node-name> key=value:effect
```
Example here
```bash
kubectl taint nodes worker app=blue:NoSchedule
```