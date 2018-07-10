# Nextcloud Quick Install
*Version 20180710.1*
This is a very quick way to install Nextcloud and setup Lets-Encrypt.  I offer both a manual and script based option. 


# Files included


# Requirements
* Ubuntu 16.04 or newer server, with SSH enabled, connected to the internet
* No current applications listening on ports 80 or 443
* Access to edge device to allow inbound access for SSL cert


# Brief



# Automatic installation



# Manual Installation

1. Connect to server via SSH.
2. Update the system.

>sudo apt update && sudo apt upgrade && sudo apt dist-upgrade    

3. Install Nextcloud via Snapcraft.

>sudo snap install nextcloud

4. The installer will collect some information and complete the install. Open a browser and navigate to the server's IP address to complete the NextCloud setup.
5. Enable HTTPS via Lets-Encrypt.

>sudo nextcloud.enable-https lets-encrypt

6. The installer will collect some information and install certificate. Once complete, add trusted ingress routes for Nextcloud to respond to in this format:
5. Add trusted ingress routes for Nextcloud to respond to in this format:
    array (    
        0 => 'LocalIP',    
        1 => 'WanIP',    
        2 => 'ExternalDomain1',    
        3 => 'ExternalDomain2',    
