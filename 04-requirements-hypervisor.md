# Hypervisor

We are going to configure now the hypervisor to deploy RHEL for Edge in a virtual machine.

A Fedora/RHEL/CentOS computer which with the capability to create Virtual Machines using KVM is needed.

## Hypervisor configuration (KVM under RHEL family)

Follow these steps:

* RHEL 9 iso must be present in the hypervisor. You must configure [hypevisor.yaml](ansible/group_vars/hypevisor.yaml) with the iso path:

  ```yaml
  rhel_iso: '/opt/isos/rhel-baseos-9.0-x86_64-dvd.iso'
  ```
* SSH must be running and one user must be configured with passwordless sudo to be used by ansible.
* Edit the [inventory file](ansible/hosts) and under inventory group **hypervisor** replace **192.168.1.200** by your hypervisor's IP. Configure the **ansible_user** accordingly, as well.
* Edit the [group_vars/hypervisor.yaml](ansible/group_vars/hypervisor.yaml) file to configure the network for the RHEL for Edge server that will be deployed in the hypervisor using the RHEL for Edge image you have just created:
  
  ```yaml
  rheledge_hostname: 'rheledge.acme.es'
  rheledge_ip: '192.168.1.134'
  rheledge_netmask: '255.255.255.0'
  rheledge_gw: '192.168.1.1'
  rheledge_dns: '8.8.8.8'
  ```
* Edit the inventory file [ansible/hosts](ansible/hosts) and configure the RHEL for Edge IP in the **rheledge** group:

  ```ini
  [rheledge]
  192.168.1.134 ansible_user=core
  ```
* The **/tmp** filesystem must have at least twice of RHEL iso size free.
* On your ansible controller node execute:
  
  ```console
  $ ansible-playbook -i hosts -l hypervisor prerequisites_hypervisor.yaml
  ```

The hypervisor will be configured and a boot iso is created which will be used to deploy a Virtual Machine using the RHEL for Edge image.

## Hypervisor configuration (other hypervisors)

If you are not using a RHEL family based hypervisor, such Debian or Suse you will need to adapt the playbooks or follow the steps manually.

Maybe the best solution in this case, even for those using VMware or Virtual Box to deploy VMs, is:

* Use the RHEL server machine to create the boot iso.
* Download the boot iso from the RHEL server and use it to create the RHEL for Edge Virtual Machine.

If you decide to do the above:

* Edit the [inventory file](ansible/hosts) and under inventory group **hypervisor** replace **192.168.1.200** by your RHEL server's IP. Configure the **ansible_user** accordingly, as well.
* Edit the [group_vars/hypervisor.yaml](ansible/group_vars/hypervisor.yaml) file to configure the network for the RHEL for Edge server that will be deployed in the hypervisor using the RHEL for Edge image you have just created:
  ```yaml
  rheledge_hostname: 'rheledge.acme.es'
  rheledge_ip: '192.168.1.134'
  rheledge_netmask: '255.255.255.0'
  rheledge_gw: '192.168.1.1'
  rheledge_dns: '8.8.8.8'
  ```
* A RHEL 9 iso must be uploaded to the RHEL server.
* The **/tmp** filesystem must have at least twice of RHEL iso size free.
* On your ansible controller node execute:
  ```console
  $ ansible-playbook -i hosts -l hypervisor prerequisites_hypervisor.yaml
  ```
    > ![TIP](icons/tip-icon.png) You can also configure the RHEL server as your ansible controller node. Just install **ansible** and configure users for ansible connections.
