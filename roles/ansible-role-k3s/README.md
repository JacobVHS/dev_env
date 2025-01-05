### ANSIBLE-ROLE-K3s

---

## Overview

This Ansible role automates the setup of a K3s Kubernetes cluster on Raspberry Pi OS devices. It dynamically fetches the cluster token from the master node and configures worker nodes to join the cluster. The role ensures that all prerequisites are met, including enabling cgroup v2, and performs necessary validations for architecture and operating system compatibility.

---

## Features

- Verifies that the architecture is `arm64` (aarch64).
- Ensures the operating system is Raspberry Pi OS.
- Configures kernel parameters to enable cgroup v2.
- Installs K3s on master nodes.
- Dynamically retrieves the cluster token from the master node.
- Configures worker nodes to join the K3s cluster.
- Handles reboots if kernel changes are applied.

---

## Requirements

- Target nodes must run Raspberry Pi OS.
- Architecture must be `arm64` (aarch64).
- SSH access with sudo privileges on all nodes.
- Master node must expose the `/var/lib/rancher/k3s/server/node-token` file.

---

## Role Variables

| Variable   | Description                               | Default                              |
|------------|-------------------------------------------|--------------------------------------|
| `k3s_url`  | The URL of the K3s server (master node).  | `https://{{ groups['master'][0] }}:6443` |
| `k3s_token`| Token to join the K3s cluster.            | Automatically fetched from the master node. |

---

## Usage

### Inventory File

Define your inventory file (`inventory.yml`) to specify master and worker nodes:

```yaml
all:
  children:
    master:
      hosts:
        master-node:
          ansible_host: 192.168.1.100
          ansible_user: pi
          ansible_become: true
    workers:
      hosts:
        worker1:
          ansible_host: 192.168.1.101
          ansible_user: pi
          ansible_become: true
        worker2:
          ansible_host: 192.168.1.102
          ansible_user: pi
          ansible_become: true
```

---

### Playbook

Use the role in a playbook:

```yaml
- name: Setup K3s Cluster
  hosts: all
  roles:
    - JacobVHS.ansible-role-k3s
```

---

### Run the Playbook

Execute the playbook with:

```bash
ansible-playbook -i inventory.yml playbook.yml
```

---

## Role Details

### Tasks

1. **Validation**
   - Ensures the target system is running `arm64` architecture.
   - Validates that the operating system is Raspberry Pi OS.

2. **Kernel Configuration**
   - Adds necessary kernel parameters (`cgroup_enable=memory cgroup_memory=1 systemd.unified_cgroup_hierarchy=1`).
   - Reboots the system if required.

3. **K3s Installation**
   - Installs K3s on master nodes using the official K3s installation script.
   - Fetches the node token from the master node.

4. **Worker Node Configuration**
   - Joins worker nodes to the cluster using the dynamically fetched token and master node URL.

---

### Dynamic Token Retrieval

The role automatically fetches the node token (`/var/lib/rancher/k3s/server/node-token`) from the master node and uses it to configure worker nodes. This eliminates the need for manual token management.

---

## Example Output

- Master Node: Installs K3s and retrieves the cluster token.
- Worker Nodes: Connect to the cluster and register as agents.

```plaintext
TASK [Install K3s on master node] ***********************************************
ok: [master-node]

TASK [Fetch node token from master] *********************************************
ok: [master-node]

TASK [Join K3s cluster on worker node] ******************************************
ok: [worker1]
ok: [worker2]
```

---

## License

This project is licensed under the MIT License.

---

## Author

Jacob Schreuder 

Contributions are welcome! Feel free to open an issue or submit a pull request to improve this role. 😊