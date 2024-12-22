# Web Server Provisioning and Deployment  

This repository documents the step-by-step process of provisioning a Linux server, configuring a web server, deploying a static website, and setting up networking and HTTPS.  


## Public Access  
You can access the deployed website using the URL:  
[https://www.oyinboboyedev.cloud/] 

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
- The assets folder (containing necessary image).

### 5. Setting Up HTTPS
- Linked my Domain name "oyinboboyedev.cloud" to the server IP Address.
- Configured HTTPS using Let's Encrypt to secure the server.
- Opened up port 443 (on AWS) to allow HTTPS traffic.

Tools and Technologies Used
- AWS: For hosting the server.
- Nginx: As the web server.
- Let's Encrypt: For HTTPS setup.

