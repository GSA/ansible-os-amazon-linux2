# Amazon Linux 2

## Introduction
---------------

This ansible role will configure an Amazon Linux 2 to be GSA complaint.

This code is based on the GSA [AWS Elastic Kubernetes Service Benchmark](https://docs.google.com/spreadsheets/d/1s9DLJIVlX4eMZXpUs-RLTeCZbdtapfy9rZKb9pvuzHs/edit#gid=1253713100).

### Pre-Hardened Amazon Machine Images
ISE provides a maintained and hardened Amazon Linux v2.0 AMI. More information about usage can be found [here](https://cautious-happiness-f7ecfe89.pages.github.io/techdoc_hardenedami_introduction.html)

### Important Information

You should carefully read through the tasks to make sure these changes will not break your systems before running this playbook.

Role Variables
--------------
There are many role variables defined in defaults/main.yml.

##### The current default configuration will:
* Enable IPv6 settings
* Enable iptables
* Enable auditing with rsyslog.
* Lock users inactive for over 30 days.

##### The configuration will not:
* Install and configure AIDE
* Install and configure NTP
* Configure the /etc/group wheel configurations

Other settings and services are listed. Please review to ensure they meet your organizational requirements.

Note, a subset of controls were removed due to operational impact or organizational dependent variables. Those are listed [here](https://github.com/GSA/ansible-os-amazon-linux2/blob/master/misc/compliance_settings.md).


### Dependencies
Ansible >= 2.7

### Example Playbook

```
---
- name: Harden Server
  hosts: all
  become: yes

  roles:
    - ansible-os-amazon-linux2
```
### How to test locally

```
ansible-playbook playbook.yml --connection=local
```

### License

BSD.
