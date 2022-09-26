# Ansible-HAproxy-Roles
Tested on: `RedHat 8`
Ansible project for installation and configuration of HAproxy service


### Step 1: Create SSH key
 * Create own ssh-key `ssh-keygen -t ed25519`
    Inside `ls ~/.ssh/` are created  id_ed25519.pub (public) and  id_ed25519 (private) key

* Copy id_ed25519.pub to target machine

### Step 2: Modify ansible.cfg
remote_user - ansible login user to which you have created and copyed id_ed25519.pub key
private_key_file - path to id_ed25519 private key, remote_user will use it to login on target machine

### Step 3: Modify inventory.ini
inventory.ini - put up address of target machine to which HAproxy will be installed

### Step 4: Modify variables inside roles haproxy/defaults/main.yml
haproxy_frontend_bind_address - frontend ip address of HAproxy machine
haproxy_backend_servers - backend servers who will handle tasks, example Apache server /httpd

### Step 5: Check Ansible playbook
```bash
ansible-playbook run.yml --check -vvv
```

### Step 6: Start Ansible playbook
```bash
ansible-playbook run.yml -v
```