# Small-Scale CI/CD Project on AWS

![CI/CD Pipeline Banner](https://via.placeholder.com/1200x300?text=CI/CD+Pipeline+on+AWS) <!-- Replace with actual banner image if available -->

## Table of Contents

- [Project Overview](#project-overview)
- [Infrastructure Setup](#infrastructure-setup)
- [Source Code Management](#source-code-management)
- [CI/CD Pipeline Configuration](#cicd-pipeline-configuration)
- [Deployment Workflow](#deployment-workflow)
- [Security and Networking](#security-and-networking)
- [Challenges and Resolutions](#challenges-and-resolutions)
- [Future Improvements](#future-improvements)

## Project Overview

This project demonstrates a simple end-to-end CI/CD pipeline for a Java-based web application deployed on AWS. The goal is to automate the build, test, and deployment process, showcasing DevOps practices in a small-scale environment. 

### Key Objectives:
- Automate code integration and deployment upon GitHub commits.
- Use open-source tools for building and deploying artifacts.
- Host everything on a single AWS EC2 instance for simplicity.

### Tech Stack:
- **AWS EC2**: For hosting the Jenkins server, Tomcat, and the application.
- **Maven**: Build tool for compiling and packaging the Java application.
- **Jenkins**: CI/CD server to orchestrate the pipeline.
- **Ansible**: Configuration management tool for deploying artifacts to Tomcat.
- **Tomcat**: Application server to host the deployed WAR file.
- **GitHub**: Source code repository with webhook integration.

The application is a basic Java web app (e.g., a simple servlet-based "Hello World" app).

## Infrastructure Setup

### EC2 Instance Creation
1. Log in to the AWS Management Console.
2. Navigate to EC2 Dashboard > Launch Instance.
3. Choose an Amazon Linux 2 AMI (free tier eligible).
4. Select t2.micro instance type.
5. Use default VPC and subnets (auto-assign public IP enabled).
6. Add storage: Default 8 GiB gp2 volume.
7. Add tags (e.g., Name: "CI-CD-Server").
8. Configure security group:
   - Allow SSH (port 22) from your IP.
   - Allow HTTP (port 80) from anywhere (0.0.0.0/0).
   - Allow Jenkins UI (port 8080) from your IP.
   - Allow Tomcat (port 8081) if customized, from anywhere.
9. Launch with a new or existing key pair for SSH access.

### Manual Installation via EC2 Terminal
Connect to the EC2 instance via SSH (e.g., `ssh -i key.pem ec2-user@public-ip`).

#### Install Java (required for Maven, Jenkins, Tomcat):
```bash
sudo yum update -y
sudo yum install java-1.8.0-openjdk -y
```

#### Install Maven:
```bash
sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo
sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo
sudo yum install -y apache-maven
mvn -version  # Verify installation
```

#### Install Jenkins:
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade -y
sudo yum install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Access Jenkins UI at `http://<ec2-public-ip>:8080` and complete initial setup (unlock with admin password from `/var/lib/jenkins/secrets/initialAdminPassword`).

#### Install Ansible:
```bash
sudo amazon-linux-extras install ansible2 -y
ansible --version  # Verify
```

#### Install Tomcat:
```bash
sudo yum install tomcat -y
sudo systemctl start tomcat
sudo systemctl enable tomcat
```

### Security Group Configuration
- Inbound Rules:
  - SSH: TCP 22, My IP
  - HTTP: TCP 80, 0.0.0.0/0
  - Jenkins: TCP 8080, My IP
  - Tomcat: TCP 8080 (default Tomcat port; adjust if needed), 0.0.0.0/0
- Outbound: All traffic allowed.

## Source Code Management

### GitHub Repository Setup
1. Create a new repository on GitHub (e.g., `ci-cd-demo`).
2. Clone locally: `git clone https://github.com/<username>/ci-cd-demo.git`.
3. Add your Java app source code, including `pom.xml` for Maven.
4. Commit and push: `git add . && git commit -m "Initial commit" && git push origin main`.

### Webhook Configuration
1. In GitHub repo > Settings > Webhooks > Add webhook.
2. Payload URL: `http://<ec2-public-ip>:8080/github-webhook/`
3. Content type: application/json
4. Events: Just the push event.
5. Active: Checked.
6. Add webhook.

Ensure Jenkins has the GitHub plugin installed (via Manage Jenkins > Manage Plugins).

## CI/CD Pipeline Configuration

### Jenkins Setup and Job Creation
1. Install necessary plugins: GitHub Integration, Maven Integration, Ansible.
2. Create a new Pipeline job: New Item > Pipeline > OK.
3. In Pipeline definition, select "Pipeline script from SCM".
4. SCM: Git, Repository URL: `https://github.com/<username>/ci-cd-demo.git`.
5. Script Path: `Jenkinsfile`.
6. Build Triggers: GitHub hook trigger for GITScm polling.

### Maven Integration
Maven is used to build the app. Ensure `pom.xml` is in the repo root.

Example `pom.xml` snippet:
```xml
<project>
    <groupId>com.example</groupId>
    <artifactId>demo-app</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>
    <!-- Dependencies and plugins here -->
</project>
```

In Jenkinsfile, add a stage for Maven build.

### Ansible Playbook for Deployment
Create an Ansible playbook in the repo (e.g., `deploy.yml`).

Example `deploy.yml`:
```yaml
---
- name: Deploy to Tomcat
  hosts: localhost
  tasks:
    - name: Copy WAR to Tomcat
      copy:
        src: target/demo-app.war
        dest: /var/lib/tomcat/webapps/
        remote_src: yes
    - name: Restart Tomcat
      service:
        name: tomcat
        state: restarted
```

In Jenkinsfile, invoke Ansible after build.

## Deployment Workflow

### Step-by-Step Flow
1. **GitHub Commit**: Developer pushes code to the main branch.
2. **Jenkins Trigger**: Webhook notifies Jenkins, triggering the pipeline.
3. **Maven Build**: Jenkins checks out code, runs `mvn clean package` to build WAR.
4. **Ansible Deploy**: Ansible copies the WAR to Tomcat's webapps directory and restarts Tomcat.
5. **Tomcat Serve**: Application is live at `http://<ec2-public-ip>:8080/demo-app`.

### Code Snippets

#### Jenkinsfile
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                ansiblePlaybook(
                    playbook: 'deploy.yml',
                    inventory: 'localhost,',
                    become: true
                )
            }
        }
    }
}
```

#### Ansible Playbook (deploy.yml)
See above example.

#### Maven Configuration (pom.xml)
See above snippet.

<!-- Add screenshots here if uploading images to repo, e.g., ![Jenkins Pipeline](images/jenkins-pipeline.png) -->

## Security and Networking

### IAM Roles and Key Pairs
- No custom IAM roles used; default EC2 instance profile.
- Key pair for SSH access: Generated during launch, stored securely.
- Network Access: Security groups restrict inbound traffic. VPC defaults used—no custom subnets or NACLs.

### Best Practices
- EC2: Use key-based SSH, disable password auth in `/etc/ssh/sshd_config`.
- Jenkins: Secure with user authentication (enable Security in Global Security). Use HTTPS if production-ready.
- General: Regularly update packages (`yum update`). Monitor logs with CloudWatch. Avoid running services as root.

## Challenges and Resolutions

- **EC2 Connectivity Issues**: SSH connection refused—Resolution: Verify security group allows port 22 from your IP; check instance public IP.
- **Jenkins Build Errors**: Maven not found—Resolution: Ensure Maven is in PATH; add `export PATH=$PATH:/opt/maven/bin` in Jenkins config or use Maven tool in Jenkins.
- **Ansible Deployment Issues**: Permission denied on Tomcat dir—Resolution: Run Ansible with `become: true` for sudo privileges; ensure ec2-user in tomcat group (`sudo usermod -aG tomcat ec2-user`).
- **Webhook Failures**: 404 on webhook—Resolution: Install GitHub plugin in Jenkins and ensure port 8080 is open.

## Future Improvements

- **Infrastructure as Code**: Use Terraform to automate EC2 creation and configuration for reproducibility.
- **Code Quality**: Integrate SonarQube in the Jenkins pipeline for static code analysis.
- **Containerization**: Dockerize the app and use ECS or EKS for deployment instead of direct Tomcat.
- **Scaling**: Separate Jenkins and Tomcat to different instances; add auto-scaling groups.
- **Monitoring**: Integrate Prometheus/Grafana for metrics and alerts.
- **Secrets Management**: Use AWS Secrets Manager for credentials instead of hardcoding.

---

This README is designed to be editable and self-contained. Feel free to fork the repo, add your screenshots, and customize! If you have questions, open an issue.

*Built with ❤️ by [Your Name] | LinkedIn: [Your LinkedIn] | Date: September 12, 2025*
