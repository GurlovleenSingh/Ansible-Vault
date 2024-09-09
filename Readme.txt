Using Ansible Vault in a playbook

This example will use an Ansible playbook to create a MySQL database. The root and user password will be stored securely with Ansible Vault.

First, create a vars directory.

mkdir vars
Next, create a new vault file to store the MySQL root and user password:

ansible-vault create vars/mysql_vault.yml
When prompted, enter the vault password and then add the following lines to define your passwords:

mysql_root_password: SecureRootPassword
mysql_user_password: SecureUserPassword
Next, create an Ansible playbook that uses this password to create a new MySQL database and user on a remote node.

nano mysql_setup.yml
