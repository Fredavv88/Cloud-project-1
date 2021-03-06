# :point_right: **Automated ELK Stack Deployment** :point_left:

*The files in this repository were used to configure the network depicted below.*

![alt text](https://github.com/Fredavv88/Cloud-project-1/blob/main/Diagrams/1.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:

* Description of the Topology
* Access Policies
* ELK Configuration
* Beats in Use
* Machines Being Monitored
* How to Use the Ansible Build

## **Description of the Topology** 

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting Inbound access to the network.

The configuration details of each machine may be found below. 

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| DVWA 1   | WebServer  | 10.0.0.8   | Linux            |
| DVWA 2   | WebServer  | 10.0.0.9   | Linux            |
| ELK      | Monitoring | 10.2.0.4   | Linux            |


### **Access Policies**

The machines on the internal network are not exposed to the public Internet.

Only the JUMP BOX_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 

* my IP address

Machines within the network can only be accessed by each other. The VM's 2 + 3 send traffic to the Elk server.

A summary of the access policies in place can be found in the table below.

| Name	   | Publicly Accessible |                       Allowed IP Addresses        |
|----------|---------------------|---------------------------------------------------| 
| Jump Box |       Yes           |   10.0.0.8, 10.0.0.9, 10.2.0.4,101.112.16.48      |
| VM-2	   |        NO           |	  10.0.0.8, 101.112.16.48                        |
| VM-3	   |        NO	         |    10.0.0.9, 101.112.16.48                        |

LOAD BALANCER: 10.0.0.8, 10.0.0.9

#### **Elk Configuration**

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the same script that was used to configure this machine can be used to quickly configure additional machines.

The playbook implements the following tasks:

* Install docker
* Install apt module
* Install pip3
* Install pip module
* Download and launch a docker container

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![alt text](https://github.com/Fredavv88/Cloud-project-1/blob/main/Images/DockerPs.png)

###### **Target Machines & Beats**

This ELK server is configured to monitor the following machines:

* DVWA 1 at 10.0.0.9
* DVWA 2 at 10.0.0.8
* DVWA 3 at 10.2.0.4

We have installed the following Beats on these machines:

* DVWA 1 at 10.0.0.9
* DVWA 2 at 10.0.0.8

* Filebeat
* Metricbeat
* Packetbeat

These Beats allow us to collect the following information from each machine:

* Filebeat: Filebeat detects changes to the filesystem. Specifically, we use it to collect Apache logs.
* Metricbeat: Metricbeat detects changes in system metrics, such as CPU usage. We use it to detect SSH login attempts, failed sudo escalations, and CPU/RAM statistics.
* Packetbeat: Packetbeat collects packets that pass through the NIC, similar to Wireshark. We use it to generate a trace of all activity that takes place on the network, in case later forensic analysis should be warranted.

**Using the Playbook** 

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned.

SSH into the control node and follow the steps below:

- Copy the playbook file to the Ansible Control Node
- Update the host file to include the webservers
- Run the playbook, and navigate to Kibana to check that the installation worked as expected

Example of a successful Filebeat Installation:

![alt text](https://github.com/Fredavv88/Cloud-project-1/blob/main/Images/Filebeat.png)

Kibana dashboard: 

![alt text](https://github.com/Fredavv88/Cloud-project-1/blob/main/Images/Kibana.png)

