# ELK-Stack-Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![https://github.com/danisallred/ELK-Stack-Project/blob/main/project%201%20diagram.png]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat.yml file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/danisallred/ELK-Stack-Project/blob/main/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access/traffic to the network.
-- Load balancers protects the system from DDoS attacks by shifting attack traffic. 
--Using a jump box provides secure and monitored access to the user on a single box and the ability to restrict IP's.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
--Filebeat Scans for info in log files and log events.
--Metricbeat gathers the info collected and sends them to a chosen output location. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Webserver| 10.0.0.5   | Linux            |
| Web 2    | Webserver| 10.0.0.7   | Linux            |
| ELK VM   |ELK Server| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-- Access to this machine is only allowed through my Public IP.

Machines within the network can only be accessed by SSH.
-- JumpBox -- JumpBox VM IP 10.0.0.4 / ELK IP 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IP              |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |
| ELK VM   | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automation is more efficent and reduces opportunity for mistakes to be introdcued to the system. The configuration also has been tested and troubleshooted.

The playbook implements the following tasks:

- Install: docker.io
- Install: python-pip
- Install: docker
- Command: sysctl -w vm.max_map_count=262144
- Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![Docker ps](https://github.com/danisallred/ELK-Stack-Project/blob/main/docker%20ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web1: 10.0.0.5
- Web2: 10.0.0.7

We have installed the following Beats on these machines:

- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
--Filebeat Scans for info in log files and log events.
--Metricbeat gathers the info collected and sends them to a chosen output location. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Control Node.
- Update the hosts file to include webserver and elk
- Run the playbook, and navigate to (http://20.106.74.173:5601/app/kibana) to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
