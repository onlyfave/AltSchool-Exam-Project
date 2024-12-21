# AltSchool-Exam-Project
In this project, I practically demonstrated, with well detailed steps how to provision a linux server and deploy a web application.

# Documentation: Provisioning a Linux Server and Deploying a Web Application

**Name:** Favour Onyeneke

**School ID:** ALT/SOE/024/0497

**Track:** Cloud Engineering

**School:** AltSchool Africa Karatu '24

**Project Overview**
This document details the step-by-step process of provisioning an AWS EC2 server, installing and configuring an Apache web server, deploying an HTML project from GitHub, and securing the website (onlyfav.me) using AWS Certificate Manager (ACM) and Certbot for SSL/HTTPS.



**Project Objectives**
The goal of this project is to provision a server, set up a web server, deploy an HTML landing page, and configure the necessary networking settings to make the page publicly accessible. Optional tasks include enabling HTTPS using a free SSL certificate.

Step-by-Step Documentation

# 1. Provisioning the Server

Steps:
Choose a Cloud Provider or Virtualization Platform:
Use AWS, GCP, Azure, or a virtualization tool like VirtualBox.
I chose AWS


**2. Launch an Instance:**
Log in to the AWS Management Console.
Navigate to EC2 Dashboard and click Launch Instance.
Choose an Amazon Machine Image (AMI): Select Ubuntu 22.04 LTS.
Choose an instance type: Select t2.micro (free tier eligible).

Configure instance details:
Leave the default VPC and subnet settings.
Enable Auto-assign Public IP.
Add storage: Keep the default 8GB or customize as required.

Configure security group:
Allow HTTP (port 80) and SSH (port 22).
Launch the instance and download the private key file (e.g., server-key.pem).

3. Connect to the Instance:
Open a terminal and navigate to the directory containing server-key.pem.
Run the following command to connect to the server:

![Screenshot 2024-12-19 195857](https://github.com/user-attachments/assets/d8f9be98-574a-49b8-b94e-0f5652f2ff04)


# 2. Web Server Setup

Steps:

Update the Server:

Run the following commands:

sudo apt update && sudo apt upgrade -y

![Screenshot 2024-12-19 195857](https://github.com/user-attachments/assets/f0b08d7d-f558-40fa-a4ee-9dc6d4d5b5a2)

![Screenshot 2024-12-19 201010](https://github.com/user-attachments/assets/08f3c289-cd98-410f-a0f9-e9ec08d9f482)

Install Apache Web Server:
Use the following command:
sudo apt install apache2 -y

![Screenshot 2024-12-19 201116](https://github.com/user-attachments/assets/a101bf91-aa5b-4442-a4c5-70c6fa4a6662)

Start and Enable Apache Service:

Run:

sudo systemctl start apache2
sudo systemctl enable apache2
![Screenshot 2024-12-19 201431](https://github.com/user-attachments/assets/422dec00-35e8-4c37-9e01-782df938d07a)

![Screenshot 2024-12-19 201554](https://github.com/user-attachments/assets/0c70bba4-98a2-4471-9aa1-fc0528f8932c)


Verify Apache Installation:

Access the default Apache page by visiting http://44.203.122.163 in a browser.

# 3. HTML Page Deployment

Steps:
1. Deploying the GitHub Project Files
 Created a project directory:
 mkdir AltSchool project  
 cd AltSchool project

3. Downloaded the project files from GitHub:
wget https://github.com/onlyfave/AltSchool-Project.git/main.zip


3. Installed unzip and extracted the files:
apt install unzip  
unzip main.zip

4. Moved the files to Apache’s root directory:
cd Alt-School-Project.git-main  
mv * /var/www/html/  
cd /var/www/html/  
ls -lrt

6. Restarted Apache to reflect changes:
systemctl restart apache2



# 4. Networking Configuration

Steps:
1. Allow HTTP Traffic:
Ensure the security group allows inbound traffic on port 80 (HTTP).

2. Access the Web Page:
Share the public IP address (or URL if a domain is configured) to access the page from any browser.


5. Bonus Task: Configure HTTPS (Optional)
Steps:
Install Certbot:
Run the following commands to install Certbot for Apache:
sudo apt install certbot python3-certbot-apache -y
![Screenshot 2024-12-19 204012](https://github.com/user-attachments/assets/9c407623-e427-4feb-83c4-447d2cbd04a3)

sudo certbot --apache
![Screenshot 2024-12-19 205012](https://github.com/user-attachments/assets/b529a8f9-fe27-4be5-afab-6a84c16f2829)

Follow the prompts to enter your domain name (requires a domain pointing to your server’s public IP).

Verify HTTPS Configuration:

Visit https://<Your-Domain> to confirm the SSL certificate is active.

Deliverables

Public IP Address/URL: https://44.203.122.163/


Screenshot:
![Screenshot 2024-12-19 205415](https://github.com/user-attachments/assets/d0603e7c-da0a-45f7-a7d0-985d8bbd077b)

