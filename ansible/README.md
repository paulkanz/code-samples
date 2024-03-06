# Sample Ansible IaC for initializing a six node Docker Swarm
The Swarm will have three managers (`node-[1-3]`) and three workers (`node-[4-6]`).

# To check to see if the nodes are ping'able
```
ansible-playbook -i inventory/hosts.yml playbooks/ping-nodes.yml 
```

# To Run in `check mode`
```
ansible-playbook -i inventory/hosts.yml playbooks/setup-docker-swarm.yml --diff --check
```

# When ready to apply
```
ansible-playbook -i inventory/hosts.yml playbooks/setup-docker-swarm.yml --diff
```
