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
