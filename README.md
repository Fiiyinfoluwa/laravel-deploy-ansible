# Deploying a Laravel Project on an Ubuntu 20.04 Instance

Ansible playbook to deploy a Laravel project on an Ubuntu 20.04 instance.

This playbook is tested on DigitalOcean Ubuntu 20.04 Droplet

## Requirements

* Ansible Control Node - DigitalOcean Ubuntu 20.04 Droplet with Ansible installed
* Managed Node - DigitalOcean Ubuntu Droplet

## Prerequisite

* Ansible installed on the control node
* Ansible community mysql module be installed on the control node
* Hash password for user
* Update inventory with managed node IP
* Variables are declared under vars/default.yml

## What userOnboarding.yaml does

* Creates New User with passwordless sudo rights
* Disables Password Login
* Copies Control node SSH key to the new user
* Sets timezone and host name of managed node

## What setup.yaml does

* Updates and Upgrade the server
* Installs LAMP and its dependecies
* Installs
  * ca-certificates
  * wget
  * curl
  * git
  * ufw
  * gnupg2
  * software-properties-common
* Install Composer and its dependencies
* Configure Firewall - UFW
* Clone repository
* Configure Apache vHosts
* Create MySQL user and database
* Add managed node IP to hosts file
* Migrate database
* Setup SSL with letsencrypt

## USE

* Onboard new user and setup managed node for deployemt with userOnboarding.yaml
* Deploy laravel project with setup.yaml
