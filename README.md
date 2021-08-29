# Project-1
ELK Stack project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
-	Diagrams/Project_1_Flowchart.drawio.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| WEB1     | VN       | 10.0.0.5   | Linux            |
| WEB2     | VN       | 10.0.0.6   | Linux            |
| ELK-VM   | MONITOR  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-	24.90.95.148

Machines within the network can only be accessed by the Jump Box Machine, IP address 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 24.90.95.148         |
| WEB 1    | No                  | 10.0.0.4             |
| WEB 2    | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows us to save time and spend resources elsewhere.

The playbook implements the following tasks:
- Install docker
- Install python3-pip
- Install the docker module
- Increase the virtual memory of the machine to a max map count of 262144
- Download and launch a docker ELK container
- Enable service docker on boot
 
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-	WEB1 10.0.0.5
-	WEB2 10.0.0.6

We have installed the following Beats on these machines:
   - Filebeat
   - Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file system, such as file logs and log events.
- Metricbeat collects metrics from the operating system and from services running on the server, which we use to track metrics such as CPU and memory.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/roles.
- Update the host file to include the IP address of the virtual machine you want monitored.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.
