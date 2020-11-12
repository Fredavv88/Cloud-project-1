Cloud-project-1## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text] [Network topology with ELK.pdf](https://github.com/Fredavv88/Cloud-project-1/files/5528302/Network.topology.with.ELK.pdf)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting Inbound access to the network.

The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.

Name	Function	IP Address	Operating System
Jump Box	Gateway	10.0.0.4	Linux
DVWA 1	Web Server	10.0.0.8	LINUX
DVWA 2	Web Server	10.0.0.9	LINUX
ELK	Monitoring	10.2.0.4	LINUX

Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the JUMP BOX_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
my IP address

Machines within the network can only be accessed by each other. The DVWA 1, DVWA 2 and DVWA 4 VMs send traffic to the Elk server.

A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump Box	Yes/No	
VM-3	NO	
VM-4	NO	
LOAD BAL.	YES	
ALLOWED IP ADDRESSES: JUMP BOX: 10.0.0.8, 10.0.0.9, 10.2.0.4, 101.112.103.93
VM-2: 10.0.0.8, 10.0.0.9, 10.2.0.4, 101.112.103.93
VM-3: 10.0.0.8, 10.0.0.9, 10.2.0.4, 101.112.103.93

LOAD BALANCER: 10.0.0.8, 10.0.0.9

Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the same script that was used to configure this machine can be used to quickly configure additional machines.

The playbook implements the following tasks:

Install docker
Install apt module
Install pip3
Install pip module
Download and launch a docker container


Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA 1 at 10.0.0.9
- DVWA 2 at 10.0.0.8
- DVWA 3 at 10.2.0.4

We have installed the following Beats on these machines:

Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat: Filebeat detects changes to the filesystem. Specifically, we use it to collect Apache logs.
Metricbeat: Metricbeat detects changes in system metrics, such as CPU usage. We use it to detect SSH login attempts, failed sudo escalations, and CPU/RAM statistics.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned.

SSH into the control node and follow the steps below:

- Copy the playbook file to the Ansible Control Node
- Update the host file to include the webservers
- Run the playbook, and navigate to Kibana to check that the installation worked as expected


_Which URL do you navigate to in order to check that the ELK server is running? http://[yourvmIPaddress]:5601/app/kibana
As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.

playbook-ansible "yamlfile.yml" (to run the playbook)
update the config/host files in ansible (docker container) with nano e.g. nano "metricbeat-config.yml"
