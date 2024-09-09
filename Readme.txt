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
************************************************************************
Here is the explanation:

vars_files: This directive includes the file mysql_vault.yml, where the encrypted variables are stored.
mysql_root_password: This variable stores the encrypted MySQL root password.
mysql_user_password: This variable stores the plaintext password for the new MySQL user.
mysql_db: This task creates a MySQL database named wp_db.
mysql_user: This task creates a MySQL user named wp_user with a specified password and grants privileges on the my_database.
Finally, run the playbook with the following command:

ansible-playbook mysql_setup.yml --ask-vault-pass

Before the playbook is executed, you have to enter the vault password. The playbook will then read the MySQL root password from the vault file and use it to create the database and user.
