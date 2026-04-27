# Ansible

- "inventory" file contains all the IPs of the servers which are going to be administrated

# Create a vault file with your credentials
```bash
ansible-vault create credentials.yml
```

# Add the content (will be opened with VIM, remember Insert and :wq command
```bash
ansible_password: your_actual_password
```

# Reference the inventory
```bash
[all]
192.168.1.80 ansible_port=2222 ansible_user=ubuntu
```

# Run command asking SSH password so that is not saved in the credentials
```bash
ansible all -i inventory -m ping --ask-pass
```

# Run ansible with the vault
```bash
ansible all -i inventory -m ping --ask-vault-pass
```

# Create an ansible.cfg file with the contens
```bash
[default]
inventory = inventory
```

With above, you can sdimply execute then `ansible all -m ping --ask-vault-pass`

# See available hosts
```bash
ansible all --list-hosts
```

# How to use playbooks
```bash
nano this_is_the_playbook.yml
```

Execute
```bash
ansible-playbook --ask-become-pass this_is_the_playbook.yml
```

