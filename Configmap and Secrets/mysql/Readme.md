# Commands to apply ConfigMaps and Secrets:

## To apply the ConfigMap for MySQL configuration:
```bash
kubectl apply -f mysql_conf.yaml
```
 This command creates a ConfigMap named 'mysql-config' in the 'default' namespace, which contains MySQL configuration settings.

## To apply the Secret for MySQL credentials:
```bash
kubectl apply -f mysql_secrets.yaml
```
 This command creates a Secret named 'mysql-secret' in the 'default' namespace, which securely stores the MySQL root password and user password.

## To apply the MySQL Deployment:
```bash
kubectl apply -f mysql_deploy.yaml
```
 This command creates a Deployment named 'mysql-deployment' in the 'default' namespace, which manages a single replica of the MySQL container using the specified image and environment variables.

# Summary of Files:
1. **mysql_conf.yaml**: Defines a ConfigMap for MySQL configuration settings.
2. **mysql_secrets.yaml**: Defines a Secret for storing sensitive MySQL credentials.
3. **mysql_deploy.yaml**: Defines a Deployment for running the MySQL container with the specified configuration and secrets.
