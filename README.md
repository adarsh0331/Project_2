<img width="940" height="364" alt="image" src="https://github.com/user-attachments/assets/c3d2a8b6-2ae0-428a-96b3-18c5dd7792ec" />


### 1. Prerequisites (what you need)

One t3.micro Ec2 instance   

A Git repo (GitHub) With all files

Basic commands familiarity (ssh, sudo).

### 2. Install Java & Maven (needed for Jenkins builds & Tomcat)

sudo apt install -y openjdk-11-jdk maven
java -version
mvn -v

### 3. Install Jenkins on the Jenkins server

On jenkins VM:

```
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
openjdk version "17.0.13" 2024-10-15
OpenJDK Runtime Environment (build 17.0.13+11-Debian-2)
OpenJDK 64-Bit Server VM (build 17.0.13+11-Debian-2, mixed mode, sharing)

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```


### Get the initial admin password:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword


Open browser: http://JENKINS_IP:8080 → paste password → install suggested plugins. Install at least:

Git plugin

Pipeline

Install maven & git on jenkins server if not already:

```sudo apt install -y maven git```

### 4. Install Ansible on Jenkins server 

On jenkins:

```
sudo apt update
sudo apt install -y ansible
ansible --version
```  
### 5. Run & verify

trigger the Jenkins job  Watch the console log.

Jenkins runs mvn package → produces target/myapp.war and then deploy the application in tomcat server using ansible playbook.

