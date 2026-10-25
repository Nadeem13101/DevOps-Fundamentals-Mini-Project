# DevOps Fundamentals Project

## 1. Project Overview

**Project Title:** Cloud-Based Linux Server Deployment with GitHub Version Control and Automation

**Student Name:** Nadeem Furkan  
**Batch Code:** AUG26-A530

This project demonstrates the deployment and management of a Linux web server on Amazon Web Services (AWS). An Ubuntu EC2 instance is configured to host a simple website using Apache Web Server.

Git and GitHub are used for version control and project management. Bash scripts automate server health checks, Apache service monitoring, and website backups. Linux system logs are analyzed to identify failed login attempts, SSH activity, system errors, and warning messages.

### Project Objectives
- Launch and configure an Ubuntu EC2 instance.
- Configure networking using a custom VPC and public subnet.
- Install and configure Apache Web Server.
- Deploy and access a website using the EC2 public IPv4 address.
- Manage project files using Git and GitHub.
- Automate server administration tasks using Bash scripts.
- Analyze Linux system logs and document findings.

## 2. AWS Architecture

The project uses the following AWS infrastructure:

1. **Amazon VPC:** Provides an isolated virtual network for the project.
2. **Public Subnet:** Hosts the Ubuntu EC2 instance.
3. **Internet Gateway:** Enables internet connectivity for the public subnet when routes and security rules are configured correctly.
4. **Route Table:** Routes eligible internet-bound traffic through the Internet Gateway.
5. **Security Group:** Controls inbound and outbound traffic to the EC2 instance.
6. **Amazon EC2:** Runs the Ubuntu Linux operating system.
7. **Apache Web Server:** Serves the project's HTML webpage over HTTP.
8. **GitHub:** Stores project files and version history.

### Architecture Flow

User Browser → Internet → Internet Gateway → Public Subnet → Ubuntu EC2 Instance → Apache Web Server → Website

### Required Network Access
- SSH (TCP port 22): For server administration, restricted to the administrator's IP address where possible.
- HTTP (TCP port 80): For accessing the website.
- HTTPS (TCP port 443): Optional, if HTTPS is configured.

## 3. Installation Steps

### Step 1: Update Ubuntu

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Install Required Packages

```bash
sudo apt install git apache2 curl vim -y
```

### Step 3: Check Installed Versions

```bash
git --version
apache2 -v
curl --version
```

### Step 4: Start and Enable Apache

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl status apache2
```

### Step 5: Deploy the Website

Create or edit the website file:

```bash
sudo nano /var/www/html/index.html
```

Add the project title, student name, batch code, current date, and the message:

`Hosted on AWS Ubuntu Server`

Save the file and exit the editor.

### Step 6: Verify the Website

Open a browser and enter:

`http://YOUR_EC2_PUBLIC_IPV4`

Replace the placeholder with the actual public IPv4 address of the EC2 instance. Ensure the EC2 security group permits inbound HTTP traffic on port 80.

### Step 7: Configure Git

```bash
git config --global user.name "Nadeem Furkan"
git config --global user.email "YOUR_GITHUB_EMAIL"
```

Replace the email placeholder with the email associated with your GitHub account.

### Step 8: Initialize and Upload the Project

```bash
mkdir -p ~/DevOps-Fundamentals-Project
cd ~/DevOps-Fundamentals-Project
git init
git branch -M main
git add .
git commit -m "Initial commit: DevOps Fundamentals Project"
```

Create the GitHub repository named `DevOps-Fundamentals-Project`, then connect it and push your code:

```bash
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/DevOps-Fundamentals-Project.git
git push -u origin main
```

Replace the username placeholder with your GitHub username. If the remote already exists, use `git remote set-url origin URL` instead of adding it again.

## 4. Commands Used

### Linux System Commands

| Command | Purpose |
|---|---|
| `pwd` | Display the current directory |
| `ls -la` | List files and directories |
| `cd ~` | Navigate to the home directory |
| `mkdir -p` | Create directories |
| `touch` | Create empty files |
| `cp` | Copy files |
| `chmod +x` | Make a script executable |
| `cat` | Display file contents |
| `grep` | Search text and log entries |
| `ps aux` | Display running processes |
| `free -h` | Display memory usage |
| `df -h` | Display disk usage |
| `uptime` | Display server uptime |
| `journalctl` | Inspect systemd logs |
| `systemctl status apache2` | Check Apache status |

### Git Commands

| Command | Purpose |
|---|---|
| `git init` | Initialize a repository |
| `git add .` | Stage project files |
| `git commit -m "message"` | Save a version of the changes |
| `git branch` | List branches |
| `git switch -c feature-documentation` | Create and switch to a new branch |
| `git switch main` | Switch to the main branch |
| `git merge feature-documentation` | Merge a branch into main |
| `git remote -v` | Display configured remote repositories |
| `git push -u origin main` | Push the main branch to GitHub |
| `git status` | Check the working tree status |
| `git log --oneline` | Display commit history |

## 5. Folder Structure

The project repository contains the following files and folders:

```text
DevOps-Fundamentals-Project/
├── README.md
├── index.html
├── log-report.txt
├── Bash Scripts/
│   ├── server-health.sh
│   ├── apache-monitor.sh
│   ├── website-backup.sh
│   └── log-monitor.sh
├── Project Documentation/
│   └── project-documentation.md
└── Screenshots/
    ├── aws-ec2.png
    ├── apache-website.png
    └── github-repository.png
```

The screenshot filenames above are examples. Replace them with your actual screenshot filenames. Include `log-report.txt` and the scripts only if you have created them.

## 6. Challenges Faced

The following are common challenges encountered during this type of project. Include only the challenges that actually occurred during implementation.

- **Website connectivity:** Troubleshooting browser connection errors by checking the EC2 public IPv4 address, security group rules, routing, and Apache status.
- **Apache service management:** Learning how to start, stop, restart, and verify the Apache service using `systemctl`.
- **Linux permissions:** Understanding file permissions and making Bash scripts executable using `chmod +x`.
- **Git version control:** Learning how to initialize a repository, stage files, create commits, create branches, and merge changes.
- **GitHub authentication:** Configuring Git identity and authenticating when pushing code to GitHub.
- **Log monitoring:** Locating authentication and system logs and interpreting failed login attempts, SSH activity, errors, and warnings.
- **Script troubleshooting:** Correcting file paths, permissions, and command errors during automation.

## 7. Learning Outcomes

After completing this project, I gained practical experience in:

- Linux server administration using Ubuntu.
- Launching and configuring an AWS EC2 instance.
- Understanding VPCs, public subnets, Internet Gateways, route tables, and security groups.
- Installing and managing Apache Web Server.
- Deploying and testing a static HTML webpage.
- Using Git and GitHub for version control and collaboration.
- Creating branches, committing changes, and merging code.
- Writing Bash scripts for server health checks, service monitoring, and website backups.
- Inspecting Linux authentication and system logs.
- Troubleshooting common server and website connectivity problems.
- Organizing project files and documenting technical work.

## Conclusion

This project provided hands-on experience with fundamental DevOps practices, including cloud infrastructure setup, Linux administration, web server deployment, version control, Bash automation, and log monitoring.

It established a foundation for further learning in CI/CD pipelines, configuration management, containerization, and cloud automation.

## Project Status

Completed tasks should be verified against the actual AWS environment, GitHub repository, scripts, and generated log report before submission.
