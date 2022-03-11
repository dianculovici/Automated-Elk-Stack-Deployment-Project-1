# Automated-ELK-Stack-Deployment-Project-1

Daniel Ianculovici 2/3/2022 Cybersecurity Bootcamp 
## Automated ELK Stack Deployment

*The files in this repository were used to configure the network depicted below.

![ Cloud Security Diagram](https://user-images.githubusercontent.com/25046544/157903665-b7787219-829c-4774-8833-30e18a94bfa6.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Cloud Security Diagram file may be used to install only certain pieces of it, such as Filebeat.

[filebeat-playbook.yml](https://github.com/dianculovici/Automated-Elk-Stack-Deployment-Project-1/blob/242dc7572a3960fcfe4df688e4be8449d69438c5/Ansible/filebeat-playbook.yml.txt)

[filebeat-config.yml](https://github.com/dianculovici/Automated-Elk-Stack-Deployment-Project-1/blob/40fce64f9666d1dfec0dc4143fc246613bbd5fee/Linux/filebeat-config.yml.txt)

*This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

- Load balancing ensures that the application will be highly functional, in addition to restricting high-traffic to the network.

What aspect of security do load balancers protect? 

 - Load balancing help servers prevent overloading as well as optimizes productivity and maximizes uptime.
 - It also adds resiliency by rerouting live traffic from one server to another causing it to eliminate single points of failure from attacks such as DDoS attack.

What is the advantage of a jump box?

 - Jump-Box are secured that are used for non-admin tasks. As a result, jump-box has improved into an even more comprehensive/lock-down secure admin workstation to decrease the chances of hackers/malware infection.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- What does Filebeat watch for?

  - It monitors any log file locations that you configure and directs to the Elasticsearch/Logstash for indexing.

- What does Metricbeat record?

  - It records metrics/statistics data and transports them to the output that you configure in Elasticsearch/Logstash.

The configuration details of each machine may be found below.

| Name                   |  Function |      IP Address                            | Operating System |
|------------------------|-----------|--------------------------------------------|------------------|
| Jump- Box- Provisioner |  Gateway  |  10.0.0.4(Private)//52.2##.2#8.106(Public) |       Linux      |
| ELK-VM                 | Server    | 10.1.0.4(Private)//168.##.2#8.110(Public)  |      Linux       |
| Web1                   | Server    | 10.0.0.5(Private)                          |      Linux       |
| Web2                   | Server    | 10.0.0.6(Private)                          |      Linux       |
| Web3                   | Server    | 10.0.0.7(Private)                          |      Linux       |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  - 7#.#3.2#5.1#2 (LocalHost IP address)

Machines within the network can only be accessed by Jump-Box-Provisioner.

- Which machine did you allow to access your ELK VM?

  - Jump-Box-Provisioner

- What was its IP address?

  - 10.0.0.4 (Private)

A summary of the access policies in place can be found in the table below.

|    Name                |  Publicly Accessible |      Allowed IP Addresses        |
|:----------------------:|----------------------|----------------------------------|
| Jump- Box- Provisioner |  Yes                 |  7#.#3.2#5.1#2                   |
| ELK-VM                 | Yes                  | 168.##.2#8.110                   |
| Web1                   | No                   | 10.0.0.4                         |
| Web2                   | No                   | 10.0.0.4                         |
| Web3                   | No                   | 10.0.0.4                         |

---All these VMs can only be accessed from the Jump-Box-Provisioner--

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible?

  - The main advantage of automating configuration with Ansible is YAML Playbooks as it provides a robust solution for configuration management/automation.  

The playbook implements the following tasks:
  
  - Install docker.io
  - Install python3-pip
  - Install Docker module
  - Use more memory 
  - Download and launch a docker elk container
  - Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[ELK-VM docker PS](<https://github.com/dianculovici/Automated-Elk-Stack-Deployment-Project-1/blob/c3620f8dabc0c522925ae2b0ca2f02cf6a5bc067/Images/ELK-VM%20Docker%20PS.PNG.png>) 

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- List the IP addresses of the machines you are monitoring:
 
 - Web1 (10.0.0.5) 
 - Web2 (10.0.0.6)
 - Web3 (10.0.0.7)

We have installed the following Beats on these machines:

 - [Filebeat Module Status Screenshot](<https://github.com/dianculovici/Automated-Elk-Stack-Deployment-Project-1/blob/3010f796b79a2a3419ad2984eb8ece8c0fca3adb/Images/Filebeat_Module_Status.png>)
 - [Metricbeat Module Status Screenshot](<https://github.com/dianculovici/Automated-Elk-Stack-Deployment-Project-1/blob/c1d357e33114ffd835b1de1438daf51c77ebd04a/Images/Metricbeat_Module_Status.png>)
 
These Beats allow us to collect the following information from each machine:
 
   - Filebeat is used to collect log files from specific files on remote machines. Examples of Filebeats can be files that are generated by Apache, Microsoft Azure tools, Nginx web server and MySQI databases. 

   - Metricbeat is used to collect specific metrics. It provides an analysis to see how healthy a machine is. An example would be CPU usage/Uptime.   

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

--Filebeat--
  
   -  Copy the filebeat-config.yml file to /etc/ansible/roles/files.
   -  Update the filebeat-config.yml file to include the ELK private IP in lines 1112 and 1812.
   -  Run the playbook, and navigate to http://168.##.2#8.110:5601/ (ELK-VM public IP) to check that the installation worked as expected.

--Metricbeat--

   -  Copy the metricbeat-config.yml file to/etc/ansible/roles/files.
   -  Update the metricbeat-config.yml file to include the ELK private IP in lines 70 and 104. 
   -  Run the playbook, and navigate to http://168.##.2#8.110:5601/ (ELK-VM public IP) to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

   -  Which file is the playbook? filebeat-playbook.yml 
   -  Where do you copy it? /etc/ansible/roles
   -  Which file do you update to make Ansible run the playbook on a specific machine?  /etc/ansible/hosts file (update with IP of the Virtual Machine).
   -  How do I specify which machine to install the ELK server on versus which to install Filebeat on? Two seperate groups in the etc/ansible/hosts file. One of the groups will be webservers which has the IPs of the VMs that I will install Filebeat to. The other group is named elkservers which will have the IP of the VM I will install ELK to.
   -  Which URL do you navigate to in order to check that the ELK server is running? http://168.##.2#8.110:5601/ 

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc:

<img width="1424" alt="CleanShot 2022-03-06 at 19 35 39@2x" src="https://user-images.githubusercontent.com/25046544/156949627-3f6ba351-53b4-4acb-a759-5da4fafe07e4.png">


![CleanShot 2022-03-06 at 20 00 01](https://user-images.githubusercontent.com/25046544/156950913-7eeaf9a9-9969-483f-b61f-117015c4e221.png)




