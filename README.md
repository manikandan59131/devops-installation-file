# devops-installation-file
steps to install devops set of tools

#Install Jenkins on AWS EC2
Jenkins is a self-contained Java-based program, ready to run out-of-the-box, with packages for Windows, Mac OS X and other Unix-like operating systems. As an extensible automation server, Jenkins can be used as a simple CI server or turned into the continuous delivery hub for any project.

Follow this article in Youtube
Prerequisites
EC2 RHEL 7.x Instance Get help here
With Internet Access
Security Group with Port 8080 open for internet
Java v1.8.x
Install Java
We will be using open java for our demo, Get latest version from http://openjdk.java.net/install/

yum install java-1.8*
#yum -y install java-1.8.0-openjdk
Confirm Java Version
Lets install java and set the java home

java -version
find /usr/lib/jvm/java-1.8* | head -n 3
#JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64
export JAVA_HOME
PATH=$PATH:$JAVA_HOME
# To set it permanently update your .bash_profile
source ~/.bash_profile
The output should be something like this,

[root@~]# java -version
openjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-b12)
OpenJDK 64-Bit Server VM (build 25.151-b12, mixed mode)
Install Jenkins
You can install jenkins using the rpm or by setting up the repo. We will setup the repo so that we can update it easily in future. Get latest version of jenkins from https://pkg.jenkins.io/redhat-stable/

yum -y install wget
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum -y install jenkins
Start Jenkins
# Start jenkins service
systemctl start jenkins

# Setup Jenkins to start at boot,
systemctl enable jenkins
Accessing Jenkins
By default jenkins runs at port 8080, You can access jenkins at

http://YOUR-SERVER-PUBLIC-IP:8080
Configure Jenkins
The default Username is admin
Grab the default password
Password Location:/var/lib/jenkins/secrets/initialAdminPassword
Skip Plugin Installation; We can do it later
Change admin password
Admin > Configure > Password
Configure java path
Manage Jenkins > Global Tool Configuration > JDK
Create another admin user id
Test Jenkins Jobs
Create “new item”
Enter an item name – My-First-Project
Chose Freestyle project
Under Build section Execute shell : echo "Welcome to Jenkins Demo"
Save your job
Build job
Check "console output"
Next Step
 Configure Users & Groups in Jenkins
 Secure your Jenkins Server
 Jenkins Plugin Installation
 Jenkins Master-Slave Configuration
 Setup Jenkins to run inside Tomcat Server

