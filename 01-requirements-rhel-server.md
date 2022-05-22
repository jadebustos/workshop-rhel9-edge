# RHEL 8 server

You will need the following:

* An ansible controller node to deploy the workshop.
* A virtualization software, this workshop assumes that you use KVM.
* A RHEL 8 Virtual Machine.

Clone this repository in your ansible controller node:

```console
# git clone git@github.com:jadebustos/workshop-rhel8-edge.git
```

## RHEL 8 server deployment

Deploy a RHEL 8 server as a Virtual Machine and perform the following:

* Create a VM with 2 processors, 25 GB disk and 8 GB RAM (or 4 GB).
  > ![IMPORTANT](icons/important-icon.png) Before deploying the server check the section **Hypervisor configuration (other hypervisors)** in [Requirements for hypervisor](04-requirements-hypervisor.md). If you have to use this server to create the boot iso you will need to increase the size at least the RHEL iso size three times.
* Register the server and configure the **BaseOS** and **AppStream** repos.
* Configure root user to be used with ansible (public key authentication).
* Edit the [inventory file](ansible/hosts) and under inventory group **rhelserver** replace **192.168.1.222** by your RHEL 8 server's IP.
* Configure the RHEL 8 server executing from your ansible controller node:

  ```console
  $ git clone git@github.com:jadebustos/workshop-rhel8-edge.git
  $ cd workshop-rhel8-edge/ansible
  $ ansible-playbook -i hosts -l rhelserver prerequisites_server.yaml
  ```

This server will be used to:

* Create and publish container images.
* Create and publish the RHEL Edge Images.

This playbook will configure the server, create several containers to be used in the worshop and publish them in an insecure container registry which will be deployed in the server as well.