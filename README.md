# Networking

Starter Ansible project for read-only network device discovery. The sample playbook gathers basic facts from Cisco IOS devices; it does not change device configuration.

## Requirements

- Python and Ansible (`ansible-core`)
- SSH access to the devices you are authorized to manage

Install the collections:

```sh
ansible-galaxy collection install -r requirements.yml
```

## Configure inventory and credentials

Edit `inventory.yml` and replace the documentation-only address (`192.0.2.10`) with an authorized device address. This starter is configured for Cisco IOS over `network_cli`; adjust `ansible_network_os` and the collection/playbook for your platform.

Provide credentials through environment variables rather than committing them:

```sh
export NETWORK_USERNAME='your-username'
read -s NETWORK_PASSWORD
export NETWORK_PASSWORD
```

Use a dedicated account with the minimum permissions required. SSH host-key checking is enabled in `ansible.cfg`; verify and trust device host keys through your normal process.

## Run the read-only playbook

```sh
ansible-playbook playbook.yml --limit router1
```

The playbook retrieves and prints basic device facts. Review inventory and targets before running it. Any future configuration-changing playbooks should be separately reviewed and tested in a lab before use.
