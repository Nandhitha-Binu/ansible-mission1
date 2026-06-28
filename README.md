# AWS Ansible Automation using Docker

Infrastructure automation project developed using **Ansible**, **Docker**, and **AWS EC2**. The project demonstrates Infrastructure as Code (IaC) by automating package management, Apache web server deployment, content configuration, and infrastructure recreation across multiple AWS regions.

---

## Project Overview

This project is divided into two missions.

### Mission 1

* Provision AWS EC2 instances in the **Mumbai (ap-south-1)** region.
* Configure Ansible control and managed nodes.
* Set up SSH key-based authentication.
* Execute Ansible playbooks using **ansible-navigator** inside Docker.
* Automate package installation, Apache configuration, content modification, and Git integration.

### Mission 2

* Provision a new infrastructure in the **Hyderabad (ap-south-2)** region.
* Clone the GitHub repository created in Mission 1.
* Update the inventory with the new infrastructure.
* Execute all playbooks successfully without modifying the automation logic.

---

## Architecture

```
                    AWS Mumbai (Mission 1)

                +----------------------+
                |   mumbai-control     |
                | Docker + Navigator   |
                +----------+-----------+
                           |
          -----------------+-----------------
          |                                 |
+---------------------+          +---------------------+
|  mumbai-client1     |          |  mumbai-client2     |
|      (dev)          |          |      (test)         |
+---------------------+          +---------------------+


                 AWS Hyderabad (Mission 2)

               +-----------------------+
               | hyderabad-control     |
               | Clone Git Repository  |
               +-----------+-----------+
                           |
          -----------------+-----------------
          |                                 |
+------------------------+       +------------------------+
| hyderabad-client1      |       | hyderabad-client2      |
|        (dev)           |       |        (test)          |
+------------------------+       +------------------------+
```

---

## Technologies Used

* AWS EC2
* Amazon Linux 2023
* Ansible
* ansible-navigator
* Docker
* Git & GitHub
* Apache HTTP Server
* Jinja2 Templates

---

## Repository Structure

```
ansible/
├── ansible.cfg
├── ansible-navigator.yml
├── inventory
├── ping.yml
├── packages.yml
├── issue.yml
├── custom.yml
├── myrole.yml
├── roles/
│   └── myrole/
│       ├── tasks/
│       ├── templates/
│       └── meta/
└── .gitignore
```

---

# Mission 1

### Infrastructure Setup

* Created three EC2 instances in Mumbai.
* Configured `devops` user.
* Enabled SSH key authentication.
* Configured password-less sudo.

### Ansible Configuration

* Installed Docker.
* Installed ansible-navigator.
* Configured `inventory`.
* Configured `ansible.cfg`.
* Created `ansible-navigator.yml`.
* Verified connectivity using `ping.yml`.

### Package Management

Playbook: `packages.yml`

* Install MariaDB
* Install PHP
* Install Development Tools (dev group)
* Update packages (dev group)

### Apache Role

Playbook: `myrole.yml`

* Created reusable Ansible role.
* Installed Apache.
* Deployed Jinja2 template.
* Displayed dynamic hostname and IP address.

### Content Modification

Playbook: `issue.yml`

* Development hosts → `development`
* Test hosts → `test`

### Custom Web Server

Playbook: `custom.yml`

* Configure Apache on development host.
* Create `/webdev`.
* Deploy custom web page.
* Configure symbolic link.

### Git Integration

* Initialize Git repository.
* Push project to GitHub.
* Ignore log files, artifacts and private keys using `.gitignore`.

---

# Mission 2

### Infrastructure Recreation

* Created three new EC2 instances in Hyderabad.
* Configured `clone` user.
* Installed Git.
* Installed Docker.
* Installed ansible-navigator.

### Project Recreation

* Clone GitHub repository.
* Update inventory.
* Update configuration files.
* Verify SSH connectivity.
* Execute:

  * `ping.yml`
  * `packages.yml`
  * `myrole.yml`
  * `issue.yml`
  * `custom.yml`

---

## Prerequisites

* AWS Account
* Amazon Linux 2023 EC2 instances
* Docker
* ansible-navigator
* Git
* SSH key pair

---

## Running the Project

Verify connectivity:

```bash
ansible-navigator run ping.yml -m stdout
```

Execute playbooks:

```bash
ansible-navigator run packages.yml -m stdout
ansible-navigator run myrole.yml -m stdout
ansible-navigator run issue.yml -m stdout
ansible-navigator run custom.yml -m stdout
```

---

## Project Screenshots

Add screenshots for:

* AWS EC2 instances
* Inventory file
* ansible.cfg
* Docker & ansible-navigator installation
* ping.yml execution
* packages.yml execution
* myrole.yml execution
* issue.yml execution
* custom.yml execution
* Apache web pages
* GitHub repository
* Mission 2 infrastructure
* Mission 2 playbook executions

---

## Author

**Nandhitha Binu**

DevOps Internship Project – Infrastructure Automation using Ansible, Docker and AWS EC2.
