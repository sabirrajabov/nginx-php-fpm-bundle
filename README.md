
# Nginx and PHP-FPM bundle installation via Ansible automation tool for Ubuntu servers




## After installation

After the running the automated script, the below services will be installed, stared, enabled on remote hosts an

- Nginx (Version: based on apt repositories)

- PHP (Version: based on apt repositories)

- PHP-FPM (Version: based on PHP version that installed)

## Usage

Firstly you need to change below files according to your preferences.

```
./import-config-and-certs/tasks/cert.cert         # SSL Cert file
./import-config-and-certs/tasks/key.key           # SSL Key file
./import-config-and-certs/tasks/production.conf   # Nginx configuration file

```
In this example, **cert** and its **key** are **self-signed**, the **nginx** config configured for **laravel 10** application served under ```/var/www/laravel```.

- For testing purposes, you can leave the default configuration and files. But if you run the script for remote host, next step should done.


After that you need to change hosts from 'localhost' to desired hosts based on your inventory file.
```
./install-nginx-php-bundle.yml

hosts: localhost -> hosts: desired_hosts
```

Lastly, run the below command under the repository folder.

```
ansible-playbook install-nginx-php-bundle.yml --ask-become-pass

```

```--ask-become-pass``` used for running commands with ```sudo``` permission. It will ask for become password for user to run script as root user. It means that the same user that runs the ansible playbook should be exist on remote hosts and has ```sudo``` privileges.


