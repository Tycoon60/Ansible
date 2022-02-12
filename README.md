Installing Ansible on Ubuntu

sudo apt update && sudo apt install software-properties-common && sudo add-apt-repository --yes --update ppa:ansible/ansible && sudo apt install -y ansible

Отключить проверку ключей (fingerprint) при подключении:
cat > /etc/ansible/ansible.cfg <<EOF
[defaults]
host_key_checking = False
EOF






mkdir /etc/ansible/group_vars
cat > /etc/ansible/group_vars/test <<EOF 
---
ansible_ssh_user : root
ansible_ssh_pass : LocalAdmin
EOF

cat > /etc/ansible/hosts <<EOF
[test]
172.26.15.24
EOF

Проверка: ansible test -m ping
