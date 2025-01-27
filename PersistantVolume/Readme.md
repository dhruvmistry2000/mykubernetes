# Persistent Volumes (PV) and Persistent Volume Claims (PVC) in Kubernetes

In Kubernetes, storage is a critical component for managing stateful applications. To handle storage, Kubernetes uses the concepts of Persistent Volumes (PV) and Persistent Volume Claims (PVC).

## Persistent Volume (PV)?

A Persistent Volume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes. PVs are resources in the cluster just like nodes are resources. They are independent of the lifecycle of any individual pod that uses the PV.

### Key Features of PV:
- **Lifecycle Management**: PVs exist beyond the lifecycle of individual pods.
- **Storage Types**: PVs can be backed by various storage types, including NFS, iSCSI, cloud provider storage, etc.
- **Capacity and Access Modes**: PVs have a defined capacity and access modes (ReadWriteOnce, ReadOnlyMany, ReadWriteMany).

## What is a Persistent Volume Claim (PVC)?

A Persistent Volume Claim (PVC) is a request for storage by a user. It is similar to a pod requesting a specific amount of CPU and memory. PVCs allow users to request storage without needing to know the details of the underlying storage infrastructure.

### Key Features of PVC:
- **Dynamic Binding**: When a PVC is created, Kubernetes will automatically bind it to a suitable PV that meets the requested criteria.
- **Access Modes**: PVCs can specify the access modes they require, which must be satisfied by the bound PV.
- **Size Requests**: PVCs can request specific storage sizes, and Kubernetes will find a PV that meets or exceeds this request.

## Types of Persistent Volumes (PV)

There are several types of Persistent Volumes (PV) that can be used in Kubernetes, each suited for different use cases:

1. **NFS (Network File System)**: 
   - [NFS](PersistantVolume%20with%20NFS/Readme.md) allows multiple pods to read and write to the same volume simultaneously. It is suitable for shared storage scenarios.

2. **iSCSI (Internet Small Computer Systems Interface)**: 
   - iSCSI provides block-level storage over the network. It is often used for high-performance applications that require low-latency access to storage.

3. **Cloud Provider Storage**: 
   - Many cloud providers offer their own storage solutions, such as Amazon EBS (Elastic Block Store), Google Persistent Disk, and Azure Disk Storage. These are typically managed services that integrate well with Kubernetes.

4. **Local Storage**: 
   - Local PVs are tied to a specific node and provide high performance for workloads that require low-latency access to storage. However, they are not suitable for high availability since they are not accessible from other nodes.

5. **CephFS**: 
   - CephFS is a distributed file system that provides high availability and scalability. It is suitable for large-scale applications that require robust storage solutions.

6. **GlusterFS**: 
   - GlusterFS is another distributed file system that aggregates storage from multiple servers into a single global namespace. It is designed for scalability and redundancy.

Each type of PV has its own advantages and use cases, and the choice of PV type depends on the specific requirements of the application and the underlying infrastructure.

## Example

 To create a Persistent Volume (PV) in your Kubernetes cluster, execute the following command:
```bash
kubectl apply -f pv.yaml
```

 To verify that the Persistent Volume has been created successfully, use the following command to list all PVs:
```bash
kubectl get pv
```

 To create a Persistent Volume Claim (PVC) that requests storage resources, run the command below:
```bash
kubectl apply -f pvc.yaml
```

 To check the status of the Persistent Volume Claim and ensure it is bound to a suitable PV, execute:
```bash
kubectl get pvc
```

 To deploy a pod that utilizes the PVC for storage, run the following command:
```bash
kubectl apply -f pod.yaml
```

 To confirm that the Persistent Volume is correctly connected to the pod, use the command below to describe the pod:
```bash
kubectl describe pods <pod-name>
```
