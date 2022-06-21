# jenkins-pipeline

## Server initial
Bring up a remote server in acloudguru playground
add local public ssh key into ~/.ssh/authorized_keys
set the remote connection in visualStudio code in local

## Install Jenkins
Reference https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/
```
sudo yum update -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum upgrade
sudo amazon-linux-extras install java-openjdk11 -y
sudo yum install jenkins -y
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

# ssh into agent, and exit for generating known_hosts file
cp ~/.ssh/known_hosts /var/lib/jenkins/.ssh/
cd /var/lib/jenkins/.ssh/
ssh-keygen -f ./jenkins-ssh-key

# copy public key content into agent /var/lib/jenkins/.ssh/authorized_keys
cat jenkins-ssh-key.pub

# copy private key content into Jenkins for generating a ssh key methon 
cat jenkins-ssh-key

```

## set agent in Jenkins
Bring up a remote server in acloudguru playground
```
sudo amazon-linux-extras install java-openjdk11 -y
sudo su
useradd -d /var/lib/jenkins jenkins
mkdir /var/lib/jenkins/.ssh
touch /var/lib/jenkins/.ssh/authorized_keys
# copy above public key content into authorized_keys
chown -R jenkins /var/lib/jenkins/.ssh
chmod 600 /var/lib/jenkins/.ssh/authorized_keys
chmod 700 /var/lib/jenkins/.ssh

```
# branch agent method
```
sudo su
useradd jenkins
passwd jenkins
visudo 
# search for root ALL=(ALL) ALL, add under
jenkins ALL=(ALL) NOPASSWD: ALL

#back to master, copy the public key into slave /~/.ssh/authorized_keys
ssh-copy-id jenkins@<ip>


```

# Generate the personal token in github.com
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

# host
81f34a4e71844808a673898c49b155b01c.mylabserver.com
