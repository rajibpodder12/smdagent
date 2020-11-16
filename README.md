### SMD Agent Installation : Unattended mode via Ansible

The Solution Manager Diagnostics (SMD) component of SAP Solution Manager provides all functionality to centrally analyze and monitor a complete system landscape. Data Services can be monitored by the SMD server if an SMD Agent is installed. The SMD Agent gathers information for the SMD which can then be used for root cause analysis. Information collected and sent to the SMD server includes back-end server configurations and the location of server log files.

Data Services provides support for performance and availability monitoring through CA Wily Introscope in Solution Manager Diagnostics through an integration with the NCS library. The NCS library is installed automatically with Data Services.

The following table describes the components of SMD.

Component|Notes
---------|------
SAP Solution Manager|You must have Solution Manager 7.01 SP26 or later installed
SMD Agent|A local agent (DIAGNOSTICS.AGENT) that collects and sends the information to the SMD server. This agent must be downloaded and installed on each Job Server that you want to monitor. The Data Services installation does not install this agent for you.Information about installing and configuring the agent is available at: https://support.sap.comInformation.
CA Wily Introscope|An application performance management framework. Introscope Enterprise Server is part of Solution Manager. There is no need to perform a separate installation. For more information, see https://support.sap.com
SAPOSCOL|The SAP Operating System Collector provides operating system data to the SMD and Introscope.

All of these components are available for download from http://support.sap.com/swdc

### Prerequsite ( Personal Development Box) :

1. [Python](https://www.python.org/downloads/source/)
2. [Ansible 2.9](https://releases.ansible.com/ansible)

**Noted. Internet connection is needed.**

### Ansible Basic Overview and workflow

```
Ansible consist of 3 main components:

1. Control Machine
2. Inventory
3. Playbook

The control machine manages the execution of the Playbook. It can be installed on your laptop or on any machine on the internet.

The Inventory file provides a complete list of all the target machines on which various modules are run by doing an ssh connection and install the necessary software’s.

The playbook consists of steps that the control mechanism will perform on the servers defined in the inventory file.

Very important to understand here is that Ansible interacts with all the servers defined in the inventory through the SSH protocol which is a secure method of remote login. Every operation is done and file transfer is encrypted.

```

![Controller and Target Machine](https://github.com/rajibpodder12/myfavs/blob/master/ansible/dg/node1/ansible_architecture.JPG)

### Ansible Directory Structure Hierarchy:
```
.
├── ansible.cfg
├── ansible_hosts
├── group_vars
│   └── appserver
├── host_vars
│   ├── nodevm-1
│   └── nodevm-2
├── playbook.yml
└── roles
    └── install-smdagent-role
        ├── README.md
        ├── tasks
        │   ├── fs-creation.yml
        │   ├── fs-creation.yml.lvm
        │   ├── fs-creation.yml.nfs
        │   ├── group-creation.yml
        │   ├── kernel-parameter-settings.yml
        │   ├── main.yml
        │   ├── rpm-install.yml
        │   ├── smdagent-install.yml
        │   ├── timezone-setup.yml
        │   ├── user-creation.yml
        │   └── user-limit.yml
        └── templates
            ├── installation.properties.j2
            └── start_dir.cd.j2
```
### Steps to execute the ansible playbook

```
export ANSIBLE_LOG_PATH=smdagent_installation.log
ansible-playbook -i ansible_hosts playbook.yml
```
