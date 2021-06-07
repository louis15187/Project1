# Project1
Cybersecurity Project 1 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/)

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_

The configuration details of each machine may be found below.


| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web 2    | Web Server| 10.0.0.5   | Linux            |
| Web 1    | Web Server| 10.0.0.7   | Linux            |
| ELK      | Monitoring| 10.1.0.4   | Linux            |

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

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

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

- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- Run: curl http://10.1.0.4:5601. This is the address of Kibana. If the installation succeeded, this command should print HTML to the console.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
