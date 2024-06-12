To create a comprehensive README file for your Ansible project on GitHub, you can follow this structured format. This file will guide users through the installation and configuration process. Here’s how you can structure it:

---

# Kubernetes Installation with Ansible

This project uses Ansible to automate the installation and configuration of a Kubernetes cluster. The setup includes one master node and multiple worker nodes. Below are the detailed steps to get started.

## Prerequisites

- Ensure you have Ubuntu 24.04 installed on your machines (master and worker nodes).
- Access to the internet for downloading necessary packages and cloning the repository.

## Installation Steps

Follow the steps below to clone the project repository, install necessary packages, and configure your Kubernetes cluster.

### 1. Clone the Repository

First, clone the specific branch of the repository that contains the Ansible playbooks for Kubernetes installation:

```bash
git clone -b kubernetes-install-ansible --single-branch https://github.com/david11alonso/devops.git
```

### 2. Install Required Packages

Update your package list and install the required packages using the following commands:

```bash
sudo apt update -y
sudo apt install -y sshpass
sudo apt install -y ansible
```

### 3. Configure the Inventory File

Modify the `inventory` file to specify the IP addresses of your master and worker nodes, along with the SSH user and password.

Open the `inventory` file in your favorite text editor:

```bash
nano inventory
```

Here’s an example structure for the `inventory` file:

```ini
[masters]
master ansible_host=<MASTER_IP> ansible_user=<USER> ansible_ssh_pass=<PASSWORD>

[workers]
worker1 ansible_host=<WORKER1_IP> ansible_user=<USER> ansible_ssh_pass=<PASSWORD>
worker2 ansible_host=<WORKER2_IP> ansible_user=<USER> ansible_ssh_pass=<PASSWORD>
```

Replace `<MASTER_IP>`, `<WORKER1_IP>`, `<WORKER2_IP>`, `<USER>`, and `<PASSWORD>` with the actual values for your setup.

### 4. Run Ansible Playbooks

Execute the following Ansible playbooks to install and configure your Kubernetes cluster. You will be prompted for the sudo password (become pass).

1. **Install Kubernetes on all nodes**:
   ```bash
   ansible-playbook --ask-become-pass -i inventory install_kubernetes.yml
   ```

2. **Configure the master node**:
   ```bash
   ansible-playbook --ask-become-pass -i inventory configure_master.yml
   ```

3. **Join worker nodes to the cluster**:
   ```bash
   ansible-playbook --ask-become-pass -i inventory join_workers.yml
   ```

## Notes

- Make sure SSH is enabled and properly configured on all nodes.
- Verify that all nodes can communicate with each other over the network.
- Ensure Ansible can connect to all nodes without interactive prompts by setting up passwordless SSH access or providing the necessary credentials in the `inventory` file.

For further details on Ansible and Kubernetes, refer to their official documentation:

- [Ansible Documentation](https://docs.ansible.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)

## Troubleshooting

If you encounter issues during the setup, consider checking the following:

- Verify the network connectivity between nodes.
- Ensure the SSH user has sufficient privileges to execute commands on the nodes.
- Check the logs for each playbook execution to identify and resolve any specific errors.

## Contributing

Contributions are welcome! Feel free to fork the repository and submit pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
