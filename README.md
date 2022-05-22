# Workshop Edge Computing with RHEL 9

This workshop is based in [https://github.com/RedHatGov/RFESummit2021](https://github.com/RedHatGov/RFESummit2021) and it is an adapted version to RHEL 9 for the workshop [Workshop Edge Computing with RHEL 8](https://github.com/jadebustos/workshop-rhel8-edge).

This workshop will also use playbooks from [https://github.com/MoyRivera/edge](https://github.com/MoyRivera/edge).

This repository License not applies to the contents of the repository [https://github.com/RedHatGov/RFESummit2021](https://github.com/RedHatGov/RFESummit2021).

This workshop is an introductory workshop to show how to use RHEL **Image Builder** feature to build, deploy and manage RHEL for Edge deployments.

You need to have knowledge about Linux and Ansible.

> ![IMPORTANT](icons/important-icon.png) This workshop has been tested using Fedora 35 as hypervisor and ansible controller node.

> ![IMPORTANT](icons/important-icon.png) All the playbooks should run with no problems on Fedora 35, RHEL 9 and CentOS Stream 9. Maybe some minor changes will have to be done for repositories if CentOS Stream 8 is used. The key words here are **should** and **maybe**. Remember that your definition of **minor** maybe it is not the same that mine :-P.

> ![IMPORTANT](icons/important-icon.png) If you do not have a RHEL family hypervisor you could use the RHEL 9 server for all the tasks except for running Virtual Machines as you need a virtualization techology to run this VM. In this case you will have to perform some steps manually.

## Workshop

You will need the following:

* An ansible controller node to deploy the workshop. (Your laptop for instance)
* A hypervisor, this workshop assumes that you use KVM. (Your laptop for instance)
* A RHEL 9 Virtual Machine.

Ansible playbooks will be used to deploy and configure all the infrastructure.

To enjoy the workshop follow these steps:

1. [Prepare the RHEL server](01-requirements-rhel-server.md)
2. [Create a RHEL for Edge image](02-create-image.md)
3. [How to upgrade a RHEL for Edge Image](03-image-upgrade.md)
4. [Prepare the hypervisor](04-requirements-hypervisor.md)
5. [Deploy a RHEL for Edge server](05-deploying-rhel-for-edge.md)
6. [Deploy a serverless containerized application on top of the RHEL for Edge server](06-deploying-serverless-application.md)
7. [Upgrading the serverless containerized application](07-upgrading-the-application.md)
8. [Operating System Upgrade](08-operating-system-upgrade.md)

[Do you dare?](do-you-dare.md)
