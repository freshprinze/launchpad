# Ansible Tasks

## Assumptions

- During setup of Ubuntu Server
  - A root user is created without password access
  - An additional account is created with root/sudo access (ie. serveradmin)
  - The serveradmin user will be the ansible user
- Configuring the Server using Ansible
  - This requires adding an ssh public key to the remote machines serveradmin's authorized_keys
- Configuring the Server for anbible access
  - Need to allow passwordless sudo access to the serveradmin user
  - Copy local user's (asiri) public key to serveradmin's authorized_keys
  - Then the server can be accessed as serveradmin without password but using public key authentication

## Tasks

### Setup Portainer

1. Configure SSH access

  ```sh
  ansible-playbook configure-ssh-access.yaml -l portainer_nodes --user=serveradmin -K
  ```

2. 


1. Check if hosts are reachable (note the 'lowercase k')

```sh
ansbile portainer_nodes -m ping --user=serveradmin -k
```

2. Execute playbook with root priviledges (note the 'uppercase k')

```sh
ansible-playbook adduser-sudo.yaml -l portainer_nodes --user=serveradmin -K
```
