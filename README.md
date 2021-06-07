# Project1
Cybersecurity Project 1 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://user-images.githubusercontent.com/50034238/121077856-2853a100-c7a6-11eb-89cc-583e5e2d3b0f.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible playbook file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml
  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- Using The Playbook


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs on the network and system metrics.


The configuration details of each machine may be found below.


| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web 2    | Web Server| 10.0.0.5   | Linux            |
| Web 1    | Web Server| 10.0.0.7   | Linux            |
| RoboCop  | Monitoring| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 52.149.151.20

Machines within the network can only be accessed by Web 1 and Web2. The 2VMs send traffic to the ELK server.
- Web 1 with an IP Address of 10.0.0.7 and Web 2 with an IP Address of 10.0.0.5 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 52.149.151.20        |
| ELK      | No                  | 10.0.0.1-254         |
| Web 2    | No                  | 10.0.0.1-254         |
| Web 1    | No                  | 10.0.0.1-254         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, The main advantage of automating configuration with Ansible is you can move from the jumpbox into the ansible container very easily and navigate to others if the ssh keys are updated


The playbook implements the following tasks:
- Install Docker.io
- Install python3-pip
- Install Docker Module
- Increase Virtual Memory
- Download and launch the ELK container
- Enable the docker on boot


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screen Shot Install Elk](https://user-images.githubusercontent.com/50034238/121074670-2b4c9280-c7a2-11eb-8067-360421c643b5.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 and 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat detects changes to the filesytem. It specifically collects Apache Logs.

The Playbook below installs Filebeat on Web 1 and Web 2 or the target hosts.

![Screen Shot Filebeat](https://user-images.githubusercontent.com/50034238/121075246-f55bde00-c7a2-11eb-971a-46bdb28e8a06.png)


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- The file of the playbook is located in Roles folder filebeat-playbook.yml. The playbook is copied onto Web 1 and Web 2.
- The file we update is the filebeat-config.yml. I specify which machine to install Filebeat on by changing around the filebeat-config.yml file from hosts to   webservers
- Run: curl http://10.1.0.4:5601. This is the address of Kibana. If the installation succeeded, this command should print HTML to the console.

Run ansible-playbook filebeat-playbook.yml.
