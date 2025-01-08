# Web Server Provisioning and Deployment  

This repository documents the step-by-step process of :
- provisioning a Linux server on AWS
- Installing and configuring Nginx as a web server
- Create and deploy a HTML page
- Configure networking to allow HTTP (port 80) and HTTPS (port 443) traffic 
- Secure the server with SSL encryption using Let's encrypt

Tools and Technologies Used
- AWS : Cloud platform For hosting the server.
- Ubuntu : Linux Distribution.
- Termius : SSH client.
- Nginx: As the web server.
- Let's Encrypt: To configure HTTPS for the web server using a free SSL certificate.


## Public Access  
You can access the deployed website using the URL:  
[https://www.oyinboboyedev.cloud/] 

## Step-by-Step Documentation  

### 1. Provisioning a Linux (Ubuntu) server on AWS  
1. **Log in to AWS**:  
   - Access the [AWS Management Console]

2. **Launch an EC2 Instance**:  
   - Go to **EC2 Dashboard** and click **Launch Instance**. 
   - Set the server name 
   - Select **Ubuntu Server XX.XX LTS (Free Tier eligible)** as your Amazon Machine Image (AMI).
   - Choose the architecture for your server [64-bit (x86) in this use case]  

3. **Choose an Instance Type**:  
   - Select **t2.micro** (Free Tier eligible) or a suitable instance type.  

4. **Create a new keypair**:  
   - enter a key pair name
   - Select 'RSA'key pair type
   - .pem private key file format
This creates the new key pair for the project and downloads it to your local machine. Keep the key file secure, as it will be required for SSH access. !   

5. **Set Up Security Groups**:  
   - Create or select a security group with the following inbound rules:  
     - **SSH (port 22)**
     - **HTTP (port 80)**  
     - **HTTPS (port 443)**   

6. **Add Storage**:  
   - Configure the amount of storage needed for the project [20 GiB in this use case]. 

7. **Launch the Instance**:  
   - Click **Review and Launch**, create or use an existing key pair, and download the `.pem` file.  
   - Keep the key file secure, as it will be required for SSH access.
   - With the newly created linux server running, please go back to the EC2 page > Instances (running) > and then connect to your server  

8. **Connect to Your Instance**:  
   - Locate the instance's **Public IPv4 address** in the EC2 Dashboard.  
   

### 2. Connect to your server  
- Use SSH via the SSH CLIENT **Termius** to connect:  

     ```bash
     ssh -i /path-to-your-key.pem ubuntu@your-public-ip
     ```  

     Replace `/path-to-your-key.pem` with the key file's path and `your-public-ip` with the instance's public IP.  
.
- Run the `hostnamectl` command to check the system information.


### 3. Installing and Configuring the Web server
 - Run the following command to ensure your package list is up-to-date:  
   `sudo apt update && sudo apt upgrade -y` 
 - Installed **Nginx** using the following commands:  
  `sudo apt install nginx -y`
  `sudo systemctl start nginx`
  `sudo systemctl enable nginx`
 - Verify Installation by opening your browser and navigate to your server's public IP address. You should see the default Nginx welcome page..
 **Note**:- Open up `port 80` for HTTP connection (On the AWS console, go to the EC2 page and click on security groups. Click on the security group configured for the linux server and edit the inbound rules by adding HTTP (port 80))

### 4. Deploying HTML Files and Assets
 1. Use the `scp` command to transfer the code files from your local machine securely to your server
 2. Run the following commands on the local machine terminal to securely copy the files to your server::
   `scp -i /path-to-your-key.pem /local-path-to-files/index.html ubuntu@your-server-ip:/var/www/html/`
  Replace:
   - /path-to-your-key.pem with the location of your SSH private key.
   - /local-path-to-files/ with the directory where your files are stored locally.
   - index.html
   - index.css - basic styling
   - assets- folders containing images etc
   - your-server-ip with the public IP address of your Nginx server.
 3. Set Correct Permissions on the Server using chmod fle permissions
 4. Open your browser and navigate to your server's public IP address. Your index.html file should load, and the index.css styling along with images from the assets folder should appear.

### 5. Setting Up HTTPS and Securing the server with SSL encryption using Let's encrypt
 1.  Linked my Domain name "oyinboboyedev.cloud" to the server IP Address.
 2.  Configured HTTPS using Let's Encrypt to secure the server.
    **Install Certbot** :-f you're running Ubuntu 20.04 or later, Certbot may already be available and installed via the default Ubuntu package manager (APT).
    - To confirm whether Certbot is already installed on your system run `certbot --version`
    - If it’s not installed, you can install it using: `sudo apt install certbot python3-certbot-nginx`
 3. Obtain an SSL Certificate:
   `sudo certbot --nginx -d your-domain.com -d www.your-domain.com`
 4. Restart Nginx After configuring SSL
    `sudo systemctl restart nginx`
 5. Open a browser and navigate to https://yourname.com.

**Note**:-  Open up port 443 (on AWS) to allow HTTPS traffic.



