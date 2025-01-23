# Configure NFS For Kuberenetes

Create an instance for an external volume to save the files of worker nodes. Install the NFS package on the instance and configure a mount point in the /etc/exports file. Install the NFS package on all nodes and mount it on each node. If possible, add the host entry in the /etc/hosts file on all nodes.

## Configure a mount point 

To Create mount point run ;

```bash
yum install nfs-utils -y
```
```bash
vi /etc/exports
```
 put entry in the exports file and run next cmd.
 ```bash
/mnt *(rw,sync,no_subtree_check,no_root_squash,no_all_squash
insecure)
```
```bash
systemctl enable nfs-server --now
```
```bash
exportfs -rav
```
```bash
showmount -e localhost
```

## Configure a mount point on work-node machines 


```bash
yum install nfs-utils -y
```
```bash
systemctl enable nfs-server --now
```
```bash
mount -t nfs <nfs-machine ip-addr/hostname>:<path to nfs dir in nfs server> /mnt
```
Before run mount -t nfs command allow nfs port in both worker-node machines and nfs-volume machine and allow icmp-ipv4 in all machines for ping.
```bash
vi /etc/fstab
```
entry in /etc/fstab
```bash
<nfs-server-ip>:/mnt /mnt nfs defaults 0 0
```
put entry in fstab file for mount permanently
```bash
systemctl restart nfs-server 
```
## Runs Commands on Master-node

```bash
kubectl apply -f pv-nfs.yaml
```

```bash
kubectl apply -f pvc-nfs.yaml
```

```bash
kubectl apply -f pod-nfs.yaml
```

```bash
kubectl get pods 
```
```bash
kubectl get pv 
```
```bash
kubectl get pvc
```
```bash
kubectl exec -it <podname> -- bash
```
```bash
df -h 
```
we can see mount point /mnt inside the container.