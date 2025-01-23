# Node affinity
 Node affinity is a concept in Kubernetes that helps you control the scheduling of pods based on the labels of nodes in your cluster. It's a way to express rules that determine where a pod should be scheduled, based on the node's labels, and can be used to make decisions about which node a pod should run on.

There are two types of node affinity:

1. RequiredDuringSchedulingIgnoredDuringExecution: This is a hard constraint. If the node does not meet the affinity rules, the pod will not be scheduled on that node.

2. PreferredDuringSchedulingIgnoredDuringExecution: This is a soft constraint. The scheduler will try to place the pod on a node that meets the affinity rules, but if no suitable node is found, the pod will still be scheduled on a different node.

Command to set Node Affinity:
```bash
kubectl label nodes <node-name> disktype=ssd
```