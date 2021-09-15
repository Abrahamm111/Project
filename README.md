## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)
https://drive.google.com/file/d/1DgPqcLNxfDttJuzIx4wUeg3OvQwqu-hl/view?usp=sharing
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ 
  nano /etc/ansible/pentest.yml
nano /etc/ansible/elk.yml
nano /etc/ansible/filebeat.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
 -  Jump Box minimizes the attack surface, ensures remote connections.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the config and system files.
- _TODO: What does Filebeat watch for?
monitor log files
- _TODO: What does Metricbeat record?_
collect operating files, statistics as well

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| VM 1     | DVWA     | 10.0.0.5   | LI               |
| VM 2     | DVVWA    | 10.0.0.6   | Linux            |
| VM 3    | DVWA     | 10.0.0.    | Linux             |
| ELK-1   | ELK       | 10.1.0.4    | LInux
### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the JUmp BOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
40.122.155.147
Machines within the network can only be accessed by JumpBOx.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? 10.0.07

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              |22                    |
|Vm-1      | Yes(tcp)            |  80                  |
|Vm-2      |yes(tcp)             | 80                   |
|Vm-3      | yes(tcp)            | 80                   |
|ELK      |   yes (tcp)          |     5601             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
        - rapid config, and deployment of virtual machines ensure all prescribed decurity measure
seperates OS and software updates
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
    - intall docker
   - install python
    - install python 3
download dvw and launch docker container
enable docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
Web 1 - 10.0.5
Web 2 - 10.0.6
Web 3 - 10.0.7
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
 - filebeat and metricbeat
These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
 - Filebeat: collects logs from VMS running file
 - MEtric beat: Sends the logs running on VM
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible DOcker.
- Update the ANsible file to include...
- Run the playbook, and navigate to /etc/ansible/hosts to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ ansible.cfg
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
 - /ets/ansible/hosts
- _Which URL do you navigate to in order to check that the ELK server is running?
http://<elk-server-ip>:5601/app/kibana

 - After running playbooks, you navigate to Kibana to check that the installation worked, you view filebeat date and metricbeat

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
