
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
sudo yum install -y maven
mvn -version  # Verify installation
```

#### Install Jenkins:
```bash
sudo yum update –y
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade
sudo sudo dnf install java-17-amazon-corretto -y
sudo yum install jenkins -y
sudo systemctl enable jenkins
sudo systemctl start jenkins
```

Access Jenkins UI at `http://<ec2-public-ip>:8080` and complete initial setup (unlock with admin password from `/var/lib/jenkins/secrets/initialAdminPassword`).

#### Install Ansible:
```bash
sudo yum install ansible -y
ansible --version  # Verify
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
2. **Maven Build**: Jenkins checks out code, runs `mvn clean package` to build WAR.
3. **Ansible Deploy**: Ansible copies the WAR to Tomcat's webapps directory and restarts Tomcat.
4. **Tomcat Serve**: Application is live at `http://<ec2-public-ip>:8080/demo-app`.

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

## Challenges and Resolutions

- **EC2 Connectivity Issues**: SSH connection refused—Resolution: Verify security group allows port 22 from your IP; check instance public IP.
- **Jenkins Build Errors**: Maven not found—Resolution: Ensure Maven is in PATH; add `export PATH=$PATH:/opt/maven/bin` in Jenkins config or use Maven tool in Jenkins.
- **Ansible Deployment Issues**: Permission denied on Tomcat dir—Resolution: Run Ansible with `become: true` for sudo privileges; ensure ec2-user in tomcat group (`sudo usermod -aG tomcat ec2-user`).

## Future Improvements

- **Infrastructure as Code**: Use Terraform to automate EC2 creation and configuration for reproducibility.
- **Code Quality**: Integrate SonarQube in the Jenkins pipeline for static code analysis.
- **Containerization**: Dockerize the app and use ECS or EKS for deployment instead of direct Tomcat.
- **Scaling**: Separate Jenkins and Tomcat to different instances; add auto-scaling groups.
- **Monitoring**: Integrate Prometheus/Grafana for metrics and alerts.
- **Secrets Management**: Use AWS Secrets Manager for credentials instead of hardcoding.

---
<img width="2378" height="1464" alt="image" src="https://github.com/user-attachments/assets/58215d71-bc82-47ac-8477-bb23b1e9f440" />
