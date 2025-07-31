# k3s-auto--deploy
Automated, secure Kubernetes (K3s) cluster provisioning using Ansible and Jenkins. All infrastructure and config changes are validated through CI/CD before deployment.
---
 
## 📚 Table of Contents
 
* [Overview](#overview)
* [Tech Stack](#tech-stack)
* [Project Structure](#project-structure)
* [Prerequisites](#prerequisites)
* [Getting Started](#getting-started)
* [CI/CD Pipeline](#cicd-pipeline)
* [Result](#result)
* [License](#license)
 
---
## 🧩 Overview
 
This repository sets up a remote Nginx app deployed on a kubernetes Cluster using:
 
* **Ansible** IaC tool to install, configure and deploy the app on a remote VM
* **Kubernetes** to host and orchestrate the app
* **Jenkins** to automate the test and the deployment of the cluster and the Nginx app
<img width="1024" height="1024" alt="ChatGPT Image Jul 27, 2025, 09_19_46 PM" src="https://github.com/user-attachments/assets/4961c663-2bb5-4a26-8c40-806f3a49419a" />

---
## 🛠 Tech Stack
 
| Tool           | Purpose                                                                   |
| -------------- | --------------------------------------------------------------------------|
| VirtualBox     | Hypervisor for the VMs                                                    |
| Kubernetes     | a lightweight Kubernetes cluster to deploy and manage the app             |
| Ansible        | Install k3s and deploy the app                                            |
| Jenkins        | Validates all the files and automate the deployment of the app            |
| yamllint       | Lints Kubernetes/YAML files                                               |
| ansible-lint   | Validates Ansible playbooks                                               |
| kubeval        | Validates Kubernetes manifests                                            |

---
## 🗂 Project Structure
 
```bash
.
├── ansible/
    ├── playbook/
        ├── deploy_nginx.yaml            # Jenkins install playbook
        └── install_k3s.yaml
    ├── inventory.ini           # Jenkins install playbook
├── k3s-manifests/                      # (Optional) Kubernetes YAMLs
    ├── nginx_deployment.yaml
    └── nginx_service.yaml

---
## ✅ Prerequisites
 
Make sure you have these installed **on your local machine**:
 
* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant](https://www.vagrantup.com/)
* [Ansible](https://docs.ansible.com/)
* [Git](https://git-scm.com/)
 
Optional (for local validation):
 
```bash
pip install ansible-lint yamllint
```
 
---