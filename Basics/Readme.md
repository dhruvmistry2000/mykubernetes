# Kubernetes Configuration Overview

This folder contains various Kubernetes configuration files that define different types of resources used to manage applications in a Kubernetes cluster.

## Types of Resources

1. **Pod**:
   - The smallest deployable unit in Kubernetes, representing a single instance of a running application process. It can contain one or more containers that share the same network namespace.

2. **ReplicationController**:
   - An older concept that ensures a specified number of pod replicas are running. It is similar to a ReplicaSet but lacks the flexibility in selecting pods.

3. **ReplicaSet**:
   - Ensures that a specified number of pod replicas are running at any given time. It maintains the desired state of the application by creating or deleting pods as necessary.

4. **Deployment**:
   - Provides declarative updates to applications. It manages ReplicaSets and ensures that the desired number of pod replicas are running, allowing for easy updates and rollbacks.

5. **Service**:
   - An abstraction that defines a logical set of pods and a policy for accessing them. It enables communication between different parts of an application, allowing external access to the pods.

## ReplicationController vs ReplicaSet

- A ReplicationController is an older resource type that ensures a specified number of pod replicas are running, using a simple selector to manage pods.
- A ReplicaSet is a more advanced resource that allows for complex selection criteria using label selectors, including matchExpressions.
- ReplicaSets are often used as part of Deployments, which manage the lifecycle of ReplicaSets and provide features like rolling updates and rollbacks.
