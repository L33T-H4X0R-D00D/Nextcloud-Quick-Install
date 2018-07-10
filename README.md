# Nextcloud Quick Install
*Version 20180710.2*
This is a very quick way to install Nextcloud and setup Lets-Encrypt.  


# Files included


# Requirements
* Ubuntu 16.04 or newer server, with SSH enabled, connected to the internet
* No current applications listening on ports 80 or 443
* Access to edge device to allow inbound access for SSL cert


# Brief



#Installation

1. Connect to server via SSH.
2. Update the system.

>sudo apt update && sudo apt upgrade && sudo apt dist-upgrade    

3. Install Nextcloud via Snapcraft.

>sudo snap install nextcloud

4. The installer will collect some information and complete the install. Open a browser and navigate to the server's IP address to complete the NextCloud setup.
5. Enable HTTPS via Lets-Encrypt.

>sudo nextcloud.enable-https lets-encrypt

6. The installer will collect some information and install certificate. Once complete, add trusted ingress routes for Nextcloud to allow inbound.

sudo nano /var/snap/nextcloud/6916/nextcloud/config/config.php


5. Add trusted ingress routes for Nextcloud to respond to in this format:  sudo nano /var/snap/nextcloud/6916/nextcloud/config/config.php



     'trusted_domains' =>
      array (
                 0 => '172.16.0.186',
                 1 => '67.163.127.119',
                 2 => 'steel-cloud.com',
                 3 => 'nc.steel-cloud.com',
                ),











  'trusted_domains' =>
  array (
    0 => '172.16.0.186',
    1 => '67.163.127.119',
    2 => 'steel-cloud.com',
    3 => 'nc.steel-cloud.com',
  ),
