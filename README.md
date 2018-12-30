# Rocket.chat install and configuration

**This repository contains docker-compose.yml and nginx config file for rocket.chat.**


## SETUP
1. Host Configuration:
-
  - install docker:<br/>
     This script is meant for quick & easy installation via:

      `curl -fsSL https://get.docker.com -o get-docker.sh`<br/>
      `sh get-docker.sh`

  -  install docker-compose:<br/>
     On Linux, you can download the Docker Compose binary from Compose repository release page on GitHub. Follow instructions from the link, which is running the curl command in your terminal to download the     binaries.<br/> These step by step instructions are also included below.

     `sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`<br/>
     `sudo chmod +x /usr/local/bin/docker-compose`<br/>
     `docker-compose --version`

  - Install nginx:<br/>
    Install a pre-built Debian Package from an OS Repository

  - Update Debian repository information:<br/>
    `apt-get update`

  - Install NGINX Open Source package:<br/>
    `apt-get install nginx`

  - Verify installation with:<br/>
    `nginx -v`


2. Download and edit compose file:

    Download compose file and change domain name, port and directory for persist container data.


3. Pull docker image and run compose file

  - pull docker images:

    `docker pull mongo`<br/>
    `docker pull rocketchat/rocket.chat`

  - Verify pulled images:

    `docker images`

  - Run compose file:
 
    `docker-compose up -d`

  - monitor logs of containers:

    `docker-compose logs -f`


4. Nginx Configuration for Reverse Proxy:

Download nginx config file and edit domain name and proxy_pass port. <br/>
Install certbot and get certificate for domain name.

   - create letsencrypt certificate with certbot commands:

     `certbot certonly --standalone --preferred-challenges http -d [domain name]`

   - Create dhparam.pem and copy to /etc/ssl/certs:

     `openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048`

