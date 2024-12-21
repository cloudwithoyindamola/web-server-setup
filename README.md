# Web Server Provisioning and Deployment  

This repository documents the step-by-step process of provisioning a Linux server, configuring a web server, deploying a static website, and setting up networking and HTTPS.  


## Public Access  
You can access the deployed website using the following public IP address:  
[http://3.252.139.18/](http://3.252.139.18/)  


## Step-by-Step Documentation  

### 1. Provisioning the Server  
- Provisioned a Linux (Ubuntu) server on AWS.


### 2. Configuring Networking  
- Added an inbound rule to the security group to allow HTTP traffic (port 80).  


### 3. Installing and Configuring the Web Server  
- Installed **Nginx** using the following commands:  
  sudo apt update
  sudo apt install nginx
- Configured Nginx to serve static pages and correctly load images.

### 4. Deploying HTML Files and Assets
Deployed the following files to the /var/www/html directory:
- index.html (the main HTML file).
- index.css (for basic styling).
- The assets folder (containing necessary images).

### 5. Setting Up HTTPS
. Configured HTTPS using Let's Encrypt to secure the server.
. Obtained a domain name from Afraid.dns and linked it to the server.
Tools and Technologies Used
- AWS: For hosting the server.
- Nginx: As the web server.
- Let's Encrypt: For HTTPS setup.
- Afraid.dns: For domain name registration.
