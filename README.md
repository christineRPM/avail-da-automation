# Avail DA Testing Automation

This repository contains Ansible playbooks for automating the deployment and testing of Avail Data Availability (DA) layer with various technology stacks. These scripts help streamline the process of setting up and evaluating different DA client implementations.

## Current Tech Stack Support

- **zkSync**: Automated setup and configuration for testing Avail DA with zkSync implementation
- *(More tech stacks to be added)*

## Prerequisites

- Ansible 2.9 or higher
- SSH Pass
- SSH access to target hosts
- Python 3.x
- Target system running Ubuntu 20.04 or higher
- Avail App ID ([Get your App ID here](https://docs.availproject.org/api-reference/avail-node-api/da-create-application-key))
- Avail account with seed phrase ([Create account here](https://docs.availproject.org/user-guides/accounts))

### Installing Prerequisites

For Ubuntu/Debian:
```bash
# Add Ansible repository
sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install sshpass
# Install Ansible
sudo apt-get install ansible

# Verify installation
ansible --version

#Install sshpass
sudo apt-get install sshpass
```

For MacOS:
```bash
# Using Homebrew
brew install ansible

# Verify installation
ansible --version

#Install sshpass
brew install sshpass
```

For other operating systems, please refer to the [official Ansible documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

## Repository Structure

```
.
├── inventory/         # Host definitions
├── playbooks/        # Ansible playbooks for different tech stacks
└── requirements.yml  # Required Ansible collections and roles
```

## Available Playbooks

### zkSync Integration
Location: `playbooks/deploy-zksync-availda.yml`

This playbook automates:
- Installation of zkSync dependencies
- Configuration of Avail DA client
- Setup of necessary networking components
- Integration with zkSync environment

During the setup process, you will be prompted for the following information:

1. **Server Configuration**
   - Your Ubuntu server IP address (replace `your_server_ip` in the command)
   - Your sudo password for server access

2. **Network Settings**
   - Chain name (default: zk-avail-testnet)
   - Your Avail App ID (obtain from [Avail Node API documentation](https://docs.availproject.org/api-reference/avail-node-api/da-create-application-key))

3. **Wallet Configuration**
   - Whether to use a seed phrase (yes/no)
   - Your seed phrase (if you selected yes) ([Learn how to create an Avail account](https://docs.availproject.org/user-guides/accounts))

Usage:
```bash
ansible-playbook playbooks/deploy-zksync-availda.yml -i inventory/hosts.yml
```

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/christineRPM/avail-da-automation.git
   cd avail-da-automation
   ```

2. Update the inventory file with your target hosts:
   ```yaml
   # inventory/hosts.yml
   all:
     hosts:
       your-target-host:
         ansible_host: your-ip-address
         ansible_user: your-ssh-user
   ```

3. Before running the playbook, make sure you have:
   - Created an Avail account and saved your seed phrase
   - Generated your Avail App ID
   - Your server's sudo password ready

4. Run the zkSync deployment playbook:
   ```bash
   ansible-playbook playbooks/deploy-zksync-availda.yml -i inventory/hosts.yml
   ```

## Contributing

Feel free to contribute additional tech stack implementations or improvements:

1. Create a new branch for your implementation
2. Add your playbook under the `playbooks/` directory
3. Update this README with relevant documentation
4. Submit a pull request

## License

MIT License
