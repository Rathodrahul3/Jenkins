# Install Jenkins on AWS EC2
Jenkins is an open-source automation server that integrates with a number of AWS Services, including: AWS CodeCommit, AWS CodeDeploy, Amazon EC2 Spot, and Amazon EC2 Fleet. You can use Amazon Elastic Compute Cloud (Amazon EC2) to deploy a Jenkins application on AWS.

## Prerequisites
1. EC2 Instance 
   - With Internet Access
   - Security Group with Port `8080` open for internet
2. As Jenkins is developed in Java, the server that will run Jenkins should have Java Installed.


## Install Jenkins
   Get the latest version of jenkins from https://pkg.jenkins.io/redhat-stable/ 
   
### Run the below commands to install Java and Jenkins
 
  1. Install Java
   ```
   amazon-linux-extras install epel 
   amazon-linux-extras install java-openjdk11  
   ```
  2. Verify Java is Installed
   ```
   java -version
   ```
  3. Now, you can proceed with installing Jenkins
   ```
   sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
   sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
   sudo yum update
   sudo yum install jenkins
   ```
  4. Start Jenkins
   ```
   #Start jenkins service
   sudo systemctl start jenkins
   
   # Setup Jenkins to start at boot.
   sudo systemctl enable jenkins
    ```
  5. Login to Jenkins.
  By default jenkins runs at port `8080`, You can access jenkins at 
   ```sh
  http://YOUR-SERVER-PUBLIC-IP:8080
   ```
## Configure Jenkins
- After you login to Jenkins,
- Run the command to copy the Jenkins Admin Password 
- Password Location:`/var/lib/jenkins/secrets/initialAdminPassword`
- Install suggested plugins; Wait for the Jenkins to Install suggested plugins
- Create First Admin User or Skip the step [If you want to use this Jenkins instance for future use-cases as well, better to create admin user]
- Add jenkins user in linux to sudoers group. `sudo usermod -a -G wheel jenkins`

### Jenkins Installation is Successful!!!!!

## Test Jenkins Jobs
1. Create “new item”
1. Enter an item name – `My-First-Project`
   - Chose `Freestyle` project
1. Under the Build section
	Execute shell: echo "Welcome to Jenkins Demo"
1. Save your job 
1. Build job
1. Check "console output"
