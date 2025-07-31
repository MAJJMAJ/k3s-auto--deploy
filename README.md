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
 
Make sure you have these installed on your local machine:

* [VirtualBox](https://www.virtualbox.org/) to create two VMs, one worker and one master

---

## 🏁 Getting Started
 
1. **Clone the Repository**
 
```bash
git clone https://github.com/MAJJMAJ/k3s-auto--deploy.git
cd /hpe-use-case-1
```
 
2. **Launch the VM**
 
```bash
vagrant up
```
 
3. **Access the VM**
 
```bash
vagrant ssh
```
 
4. **Run the Ansible Playbooks**
 
```bash
ansible-playbook ansible/ansible-jenkins.yaml
```
 
(Optional: Install validation tools inside VM)
 
```bash
ansible-playbook ansible/install_validation_tools.yaml
```
 
---
 
## 🔄 CI/CD Pipeline
 
* Triggered automatically on `git push`
* Runs:
 
  * `yamllint` on `k8s-manifests/`
  * `ansible-lint` on `ansible/`
* Validates Ansible syntax, FQCN usage, idempotency, and YAML formatting
<img width="1536" height="1024" alt="ChatGPT Image Jul 27, 2025, 09_33_49 PM" src="https://github.com/user-attachments/assets/b0699f8d-d94f-4e7f-8d43-121e98f5d89c" />
 
---
 
## 🌐 Result
 
* Jenkins is installed and running on port `8080` of the VM
* Playbooks follow best practices (FQCN, idempotency)
* CI/CD ensures your infrastructure code remains clean and consistent