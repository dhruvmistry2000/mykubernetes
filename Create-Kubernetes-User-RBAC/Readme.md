
## What is RBAC?
Role-Based Access Control (RBAC) in Kubernetes is a security mechanism that regulates access to resources based on roles assigned to users. It helps control what actions users can perform within a cluster through:
- Roles: Define permissions for resources within a namespace
- ClusterRoles: Define cluster-wide permissions
- RoleBindings: Link roles to users/groups within a namespace
- ClusterRoleBindings: Link cluster-wide roles to users/groups

## Creating a New User with RBAC
Create a key and csr request for the user.

```bash
openssl genrsa -out sam.key 2048
openssl req -new -key sam.key -out sam.csr -subj "/CN=sam"
```
To create a signingrequest for the user first encode the csr, don't copy the % sign which is at end of line..
```bash
cat sam.csr | base64 | tr -d "\n"
S0tLS1CRUdJTiBDRVJUSUZJQ0FURSBSRVFVRVNULS0tLS0KTU%
```
Create the CertificateSigningRequest, add the base64 encoded csr next to the request field.
```bash
cat signingrequest.yaml
```
Paste this and enter you base64 encoded csr in the request sectiom.
```bash
apiVersion: certificates.k8s.io/v1
kind: CertificateSigningRequest
metadata:
  name: sam-csr
spec:
  signerName: kubernetes.io/kubelet-serving
  request: <BASE64-ENCODED-CSR>
  expirationSeconds: 86400  # one day
  usages:
  - client auth
```
```bash
kubectl apply -f signingrequest.yaml
```

Once applied and CertificateSigningRequest created list and Approve the csr

```bash
kubectl get csr
kubectl certificate approve sam-csr
```
Get the crt
```bash
kubectl get csr sam-csr -o jsonpath='{.status.certificate}' | base64 -d > sam.crt
```
Set context for the user.
```
kubectl config set-credentials sam --client-certificate=sam.crt --client-key=sam.key
kubectl config set-context sam-context --cluster=<cluster-name> --user=sam
kubectl config use-context sam-context
```
Now try to login with user and try to list nodes or pods.
```bash
kubectl config use-context sam-context
kubectl get nodes
Error from server (Forbidden): nodes is forbidden: User "sam" cannot list resource "nodes" in API group "" at the cluster scope
```
Now login back with kubeadmin and create a role and rolebinding 
```bash
kubectl config use-context minikube
kubectl create role example-role --verb=get --verb=list --verb=watch --resource=pods --namespace=default
kubectl create rolebinding example-role-binding1 --role=example-role --user=sam
```
Now login again with sam user and check if user got the permissions.
```bash
kubectl config use-context sam-context
kubectl get pods
```
How delete new added contetx
```bash
kubectl config delete-context sam-context
```

how to see context
```bash
kubectl config get-contexts
```
How we see the current cluster name 

```bash
kubectl config get-contexts
```