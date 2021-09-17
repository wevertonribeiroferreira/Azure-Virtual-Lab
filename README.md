# Elk-Stack-Project
My first cloud network
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.



![alt text](https://github.com/wevertonribeiroferreira/Azure-Virtual-Lab/blob/main/network_diagram.png)



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ ******************************

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. The off-loading function of a load balancer defends an organization against distributed denial-of-service attacks (DDoS). It does this by shifting attack traffic from the corporate server to a public cloud provider. Having a Jump Box has an advantage of being a secure computer that all admins first connect to before launching an administrative task or use as an origin point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function    | IP Address   | Operating System |
|----------|-------------|--------------|------------------|
| Jump Box | Gateway     | 104.43.207.88| Linux            |
| Web-1    | Web Server  | 10.0.0.5     | Linux            |
| Web-2    | Web Server  | 10.0.0.6     | Linux            |
| DVWA     | Container   |      -       | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- My personal IP Address.

Machines within the network can only be accessed by Jump Box machine.
- You can also access the Elk Server through the Jumpbox. (20.85.232.3)

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump-Box  |         Yes         |       10.0.0.4       |
| Elk Server|         Yes         |       10.1.0.4       |
| Web-1     |         No          |   Static IP Address  |
| Web-2     |         No          |   Static IP Address  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible lets you model even highly complex IT workflows. You can put together the entire application environment no matter where it's deployed.************************

The playbook implements the following tasks:
- Install Docker
- Increase Virtual Memory
- Download and Launch Elk Container
- Open ports 5601, 9200, & 5044
- Enable service docker on boot


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker](https://github.com/wevertonribeiroferreira/Azure-Virtual-Lab/blob/main/elk.PNG) ******************************

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 - 10.0.0.5
- Web-2 - 10.0.0.6

We have installed the following Beats on these machines:
- Web-1 - 10.0.0.5
- Web-2 - 10.0.0.6

These Beats allow us to collect the following information from each machine:
- The Beats gather the logs and metrics from my environment and documents them with essential metadata from hosts, container platforms like Docker, and cloud providers before shipping them to the Elastic Stack. (Example below)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 


SSH into the control node and follow the steps below:

- Copy the `elkserver.yml` file to `/etc/ansible` directory.
- Update the `hosts` file to include your elk server's ip address.
- Run the playbook, and navigate to the kibana page 'http://20.85.232.3:5601/app/kibana' to check that the installation worked as expected.



***


_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
