# install-Jenkins
## Prerequisites

Java Installation: Jenkins requires Java to run. Ensure that you have Java installed on your system. Jenkins supports Java versions 11 and 17.

To install OpenJDK, run:
```bash
sudo yum install java-11-openjdk-devel -y
```

Verify Java installation:
```bash
java -version
```

System Update: Update your system packages.
```bash
sudo yum update -y
```

## Step-by-Step Installation

### Add Jenkins Repository

First, add the Jenkins repository to your system. This allows you to install Jenkins from its repository and receive updates directly.
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```

### Install Jenkins

Install Jenkins using the Yum package manager:
```bash
sudo yum install jenkins -y
```

### Start and Enable Jenkins

Once installed, start the Jenkins service and enable it to start on boot:
```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Adjust Firewall

If you have a firewall enabled, you'll need to allow traffic on port 8080 (default Jenkins port):
```bash
sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
sudo firewall-cmd --reload
```

### Access Jenkins

Open a web browser and navigate to http://your-server-ip:8080. You should see the Jenkins setup screen.

### Unlock Jenkins

During the initial setup, Jenkins requires an unlock key. Retrieve this by running:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Copy and paste this key into the web interface to continue.

###  Install Suggested Plugins

After unlocking Jenkins, you can choose to install the suggested plugins or select specific ones based on your needs. The suggested plugins cover most use cases.

### Create an Admin User

Once the plugins are installed, create an admin user and configure the instance.

### jenkins is Ready

Your Jenkins instance is now up and running. You can start creating jobs and pipelines!

## Troubleshooting
- ava Version Issues: Ensure that you are running a compatible Java version (11 or 17).
- Firewall Issues: Make sure port 8080 is open and accessible from your network.
- Service Status: If Jenkins does not start, check the service status using sudo systemctl status jenkins.

## Conclusion
Jenkins is now installed and ready to use on your Yum-based Linux server. Refer to the Jenkins documentation for more advanced configuration and usage.

# Jenkins Installation on Windows

## Prerequisites

Java Installation: Jenkins requires Java to run. It supports Java versions 11 and 17. Ensure Java is installed on your system.
- Download Java: Go to the Adoptium website and download the latest OpenJDK version 11 or 17.
- Install Java: Run the installer and follow the instructions. Make sure to set the JAVA_HOME environment variable to the Java installation path.

Verify Java installation by opening a Command Prompt and running:
```bash
java -version
```
System Requirements: Ensure your system meets the minimum requirements for running Jenkins.

## Step-by-Step Installation

### 1. Download Jenkins
- Visit the Jenkins download page.
- Click on the "Windows" link to download the Jenkins Windows installer (a .msi file).
  
### 2. Run the Installer
- Locate the downloaded .msi file and double-click to run it.
- Follow the installation wizard steps to install Jenkins.

### 3. Choose Installation Path
- During the installation, you will be prompted to select the installation directory for Jenkins. The default is usually C:\Program Files\Jenkins.

### 4. Set Jenkins as a Windows Service
- The installer will automatically set up Jenkins to run as a Windows service. This means Jenkins will start automatically whenever Windows starts.

### 5. Open Port 8080
- Jenkins uses port 8080 by default. Ensure this port is not blocked by your firewall.
- If you have a firewall enabled, you may need to create an inbound rule to allow traffic on port 8080.

### 6. Complete Installation
- After the installation is complete, Jenkins will automatically start. You can verify this by going to http://localhost:8080 in your web browser.

### 7. Unlock Jenkins
- During the initial setup, Jenkins requires an unlock key. You can find this key in the secrets folder of your Jenkins installation directory.

To retrieve the key, open the file:
```bash
C:\Program Files\Jenkins\secrets\initialAdminPassword
```
Copy and paste this key into the web interface to continue.

### 8. Install Suggested Plugins
- After unlocking Jenkins, you can choose to install the suggested plugins or select specific ones based on your needs. The suggested plugins cover most use cases.

### 9. Create an Admin User
Once the plugins are installed, create an admin user and configure the instance.

### 10. Jenkins is Ready
- Your Jenkins instance is now up and running. You can start creating jobs and pipelines!

## Troubleshooting
- Java Version Issues: Ensure that you are running a compatible Java version (11 or 17). Make sure the JAVA_HOME environment variable is correctly set.
- Port Issues: Ensure port 8080 is open and not used by another application.
- Service Status: If Jenkins does not start, check the Windows Services to ensure the Jenkins service is running.

## Conclusion
Jenkins is now installed and ready to use on your Windows system. Refer to the Jenkins documentation for more advanced configuration and usage.
