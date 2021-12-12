## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Diagram](https://user-images.githubusercontent.com/89557963/145701277-c0e608eb-8650-4207-b4bc-ade677265a54.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  /etc/ansible/install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- Load balancers can protect systems from unauthorized parties and attacks, such as unwanted traffic or a DDos attack.
- Jump boxes give users access to multiple virtual machines from a single node, as well as giving them the ability to monitor and conduct any necessary administrative task.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat watches for any information, such as logs and events that could have been altered.
- Metricbeat records and monitors the statistcs and data from the servers that are running.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| ELK-Stack|Elk Server| 10.1.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.7   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 76.21.80.197

Machines within the network can only be accessed by SSH.
- I allowed my Jump Box to have access to my ELK virtual machine and the private IP is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.7 10.0.0.6    |
| Web-1    | No                  | 10.0.0.4 10.0.0.6    |
| Web-2    | No                  | 10.0.0.4 10.0.0.7    |
| ELK VM   | No                  | 10.0.0.4 10.0.0.7    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage of automating the configurations for Ansible is that it allows the adminsitrator to deploy multiple servers with a single YAML playbook.

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install docker container
- Launch the docker container (ELK)
- Use the command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![elkproject part 4](https://user-images.githubusercontent.com/89557963/145701306-0227bb51-405e-4083-bdbb-9e9997c4b642.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.7
- Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Using Filebeat allows us to collect log events from the log files it monitors.
- Using Metricbeat allows us to ship the statistics it collects to a specific output.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the configuration file to include the proper webservers as well as the ELK virtual machine.
- Run the playbook, and navigate to the ELK virtual machine to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- The playbook file is a YAML file. We copy the file at /etc/ansible/files.
- We run the YAML file in order to run a playbook. We determine where to specify the file by either pathing it to webserver or elk.
- http://[51.143.21.130]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
