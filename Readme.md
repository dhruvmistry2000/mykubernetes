# Learning Kubernetes

This repository contains files that I have created during my learning journey with Kubernetes. I have documented various processes and configurations for different types of Kubernetes services and resources.
Feel free to explore the files and the configurations I have documented.

# .bashrc
While learning Kubernetes, I found myself using certain commands repeatedly. To optimize my workflow, I added some aliases in my .bashrc file. Here are the aliases I created:
```bash
alias k="kubectl"
alias ka="kubectl apply -f"
alias kg="kubectl get"
alias kgw="kubectl get pods -o wide"
```
Add them to your .bashrc file, then restart the terminal or run the following command to apply the aliases:
```bash
source .bashrc
```
