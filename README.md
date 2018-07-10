# Nextcloud Quick Install
*Version 20180710.2*
This is a very quick way to install Nextcloud and setup Lets-Encrypt.  


# Files included


# Requirements
* Ubuntu 16.04 or newer server, with SSH enabled, connected to the internet
* No current applications listening on ports 80 or 443
* Access to edge device to allow inbound access for SSL cert
* A public domain name with DNS pointed to an external IP of the Nextcloud server


# Brief



#Installation

1. Connect to server via SSH.
2. Update the system.

>sudo apt update && sudo apt upgrade && sudo apt dist-upgrade    

3. Install Nextcloud via Snapcraft.

>sudo snap install nextcloud

4. The installer will collect some information and complete the install. Open a browser and navigate to the server's IP address to complete the NextCloud setup.
5. Open inbound port 80 and/or 443 and forward them to your Nextcloud server. If you wish to only use HTTPS, only open and forward inbound 443.
6. Make certain your public DNS name resolves to the IP address you performed the port forward on in the previous step.
7. Use Lets-Encrypt to create and install a free SSL certificate for your Nextcloud install.

>sudo nextcloud.enable-https lets-encrypt

8. The installer will collect some information and install certificate. Once complete, add trusted ingress routes for Nextcloud to allow inbound.

>sudo nano /var/snap/nextcloud/6916/nextcloud/config/config.php


9. Edit the config to add your custom addresses. Use the following format.

```
'trusted_domains' =>
 array (
    0 => 'InternalIP',
    1 => 'ExternalIP',
    2 => 'PublicDomain',
    3 => 'PrivateDomain',
   ),
```

Note: You will not be able to connect to private domain names via HTTPS since Lets-Encrypt only provides certificates for public domains.


