# Flask Application Deployment with Ansible

This repository contains the necessary configuration to deploy a Flask application on multiple Amazon Linux 2 EC2 instances using Ansible and `systemd`.

## Prerequisites

- Ansible installed on your local machine or a control EC2 instance.
- An SSH key pair to connect to your EC2 instances.
- Git installed on your local machine or control EC2 instance.
- AWS EC2 instances running Amazon Linux 2.

## Repository Structure

├── ansible.cfg
├── inventory
├── setup.yml
└── README.md

## Setup Instructions

### Step 1: Configure Inventory

Edit the `inventory` file to include the IP addresses of your EC2 instances.

```ini
[all]
<ec2-instance-ip-1>
<ec2-instance-ip-2>
<ec2-instance-ip-3>

Step 2: Configure Ansible
Ensure your ansible.cfg is set to use your PEM key for SSH connections.

Example ansible.cfg:
[defaults]
inventory = ./inventory
private_key_file = /path/to/your/private-key.pem
remote_user = ec2-user
host_key_checking = False


Step 3: Write Your Ansible Playbook
The setup.yml playbook installs necessary packages, clones the Flask application from a Git repository, and sets up a systemd service to run the Flask app.

Step 4: Run the Ansible Playbook

ansible-playbook -i inventory setup.yml

