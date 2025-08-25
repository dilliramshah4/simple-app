# Simple App - DevOps 

## Description
A brief overview of the project:
- What the app does (Hello World Node.js web app).
- Why it was built (for DevOps deployment practice).
- Brief mention of technologies: Node.js, Express, AWS EC2, GitHub Actions, PM2.

## Table of Contents
- [Description](#description)
- [Deployment URL](#deployment-url)
- [Prerequisites](#prerequisites)
- [Setup and Deployment](#setup-and-deployment)
- [GitHub Actions Workflow](#github-actions-workflow)


## Deployment URL
Live app URL: http://35.154.87.219:3000/

## Prerequisites
- AWS Account with EC2 permissions
- Node.js and npm installed
- GitHub account
- SSH key pair for EC2 access
- PM2 process manager

## Setup and Deployment
- Launch an Ubuntu EC2 instance
- Configure security group for SSH (port 22) and app port (3000)
- SSH into EC2 and clone this repo (`git clone https://github.com/dilliramshah4/simple-app.git`)
- Run `npm install`
- Install PM2 globally: `sudo npm install pm2 -g`
- Start app with PM2: `pm2 start app.js --name hello-app`
- Setup PM2 to auto-start on reboot (`pm2 startup` and `pm2 save`)

## GitHub Actions Workflow
- Workflow file is in `.github/workflows/deploy.yml`
- Repository secrets used:
  - `EC2_HOST`: EC2 public IP or DNS
  - `EC2_SSH_KEY`: Private SSH key content
- Code pushes to `main` branch trigger auto-deployment via SSH to EC2


## Troubleshooting
- Check PM2 app status: `pm2 list`
- View logs: `pm2 logs hello-app`
- Verify EC2 security group rules allow traffic on app port
- Ensure app listens on `0.0.0.0` to accept external connections



