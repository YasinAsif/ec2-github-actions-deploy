# CI/CD Pipeline Implementation Report
## Automated Deployment to AWS EC2 Using GitHub Actions

---

**Student Name:** Yasin Asif  
**Date:** January 25, 2026  
**Subject:** DevOps / Cloud Computing

---

## 1. Introduction

This report documents the implementation of a Continuous Integration/Continuous Deployment (CI/CD) pipeline that automatically deploys a web application to an Amazon EC2 instance whenever code is pushed to a GitHub repository.

## 2. Objective

To automate the deployment process of a static website to AWS EC2 using GitHub Actions, eliminating manual deployment steps and ensuring consistent, reliable deployments.

## 3. Technologies Used

| Technology | Purpose |
|------------|---------|
| **AWS EC2** | Cloud server hosting (Ubuntu 24.04, t3.micro) |
| **GitHub Actions** | CI/CD automation platform |
| **Nginx** | Web server for serving static files |
| **Git** | Version control system |
| **SSH** | Secure connection between GitHub and EC2 |

## 4. Implementation Steps

1. **EC2 Instance Setup:** Launched an Ubuntu EC2 instance in the EU-North-1 region with appropriate security group rules (ports 22 and 80).

2. **Web Server Configuration:** Installed Nginx web server and configured it to serve files from `/var/www/html`.

3. **GitHub Actions Workflow:** Created a deployment workflow (`.github/workflows/deploy.yml`) that triggers on every push to the main branch.

4. **Secure Authentication:** Configured GitHub Secrets to securely store EC2 credentials (host IP, username, and SSH private key).

5. **Automated Deployment:** The workflow uses SSH to connect to EC2 and executes `git pull` to fetch the latest code.

## 5. Workflow Architecture

```
Developer Push → GitHub Repository → GitHub Actions Trigger
                                            ↓
                                    SSH Connection to EC2
                                            ↓
                                    Git Pull Latest Code
                                            ↓
                                    Website Updated Live
```

## 6. Results

- **Live Website URL:** http://13.62.128.44
- **Deployment Time:** Approximately 15-20 seconds from push to live
- **Success Rate:** 100% after proper configuration

## 7. Challenges Faced

1. **Dynamic IP Address:** EC2 public IP changed after instance restart; resolved by updating GitHub secrets.
2. **Security Group Configuration:** Initial SSH timeout was fixed by enabling port 22 inbound rules.
3. **GitHub Token Scope:** Required adding `workflow` scope to push workflow files.

## 8. Conclusion

The CI/CD pipeline was successfully implemented, demonstrating the practical application of DevOps principles. The automation reduces deployment errors, saves time, and provides a consistent deployment process. This approach is scalable and can be extended to include testing, staging environments, and more complex deployment strategies.

---

**Repository:** https://github.com/YasinAsif/ec2-github-actions-deploy
