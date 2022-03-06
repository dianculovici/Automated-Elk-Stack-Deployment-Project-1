# Automated-ELK-Stack-Deployment-Project-1

Daniel Ianculovici 2/3/2022 Cybersecurity Bootcamp 
## Automated ELK Stack Deployment

*The files in this repository were used to configure the network depicted below.

[Cloud Security Diagram](<https://github.com/dianculovici/Automated-Elk-Stack-Deployment-Project-1/blob/ceef307bf2a4430c197954c37136b770f4800a5a/Diagrams/%20Cloud%20Security%20Diagram.png>) 

*These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Cloud Security Diagram file may be used to install only certain pieces of it, such as Filebeat.

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

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Dmn Vulnerable Web Application.

- Load balancing ensures that the application will be highly functional, in addition to restricting high-traffic to the network.

What aspect of security do load balancers protect? 

 - Load balancing help servers prevent overloading as well as optimizes productivety and maximes uptime.
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
| Jump- Box- Provisioner |  Gateway  |  10.0.0.4(Private)//52.***.2*8.106(Public) |       Linux      |
| ELK-VM                 | Server    | 10.1.0.4(Private)//168.**.2*8.110(Public)  |      Linux       |
| Web1                   | Server    | 10.0.0.5(Private)                          |      Linux       |
| Web2                   | Server    | 10.0.0.6(Private)                          |      Linux       |
| Web3                   | Server    | 10.0.0.7(Private)                          |      Linux       |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  - 73.43.2*5.1*2 (LocalHost IP address)

Machines within the network can only be accessed by Jump-Box-Provisioner.

- Which machine did you allow to access your ELK VM?

  - Jump-Box-Provisioner

- What was its IP address?

  - 10.0.0.4 

A summary of the access policies in place can be found in the table below.



