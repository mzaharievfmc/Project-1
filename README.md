# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)https://go.gliffy.com/go/share/sqq8iqsqk90y9bl8r48s

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ 
* filebeat-playbook.yml
* metricbeat-playbook.yml


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? – Defend against distributed Denial of Service attacks. Jump box provide restricted access to a network environment. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the operating system and system services.
- _TODO: What does Filebeat watch for? – Monitor and collects filelogs events and forward them for indexing.
- _TODO: What does Metricbeat record? – Collect metrics and statistics and ships them to specified output such as Elasticsearch or Logstash. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.


| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.5   | Linux            |
| Web 1    | DVWA       | 10.0.0.6   | Linux            |
| Web 2    | DVWA       | 10.0.0.7   | Linux            |
| ELK VM   | ELK/Kibana | 10.1.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box VM machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ - 20.106.246.79

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? – Jump Box 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 20.106.246.79        |
| Web 1    | No                  | 10.0.0.6             |
| Web 2    | No                  | 10.0.0.7             |
| ELK VM   | Yes                 | 40.78.143.92         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_- Create connections to VM’s inside VNet.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Create Filebeat configuration file
- Create Metricbeat configuration file
- Verify installation and playbook
  

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
* Web 1 (10.0.0.6) 
* Web 2 (10.0.0.7)

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

* Filebeats
* Metricbeats


These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

* Filebeats monitors file logs, collects log events and forwards them for indexing.

* Metricbeats records metrics nad statistics from operating system and services running on a server.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/files.
- Update the filebeat-playbook.yml file to include...
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ filebeat-playbook.yml /etc/ansible/files
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running? - htttp://40.78.143.92:5601/app/kibana/

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ 
ansible-playbook filebeat-playbook.yml
ansible-playbook metricbeat-playbook.yml
