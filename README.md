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
## token for blueocean
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

# host
81f34a4e71844808a673898c49b155b01c.mylabserver.com

# running docker in pipeline 
## install jenkins plugin
docker
docker pipeline
## install docker on node
sudo yum install docker -y
sudo chmod 666 /var/run/docker.sock
sudo usermod -aG docker jenkins
sudo systemctl restart docker

# download jenkin plugin 
updates.jenkins-ci.org/download/plugins
## downgrade the plugin
ssh into jenkins server
wget the plugin from the above link
got the *.hpi file
cd /var/lib/jenkins/plugins/
ls |grep github
*-api
*-api.jpi
mv ./github-api ./github-api.old
sudo !!
sudo mv ./github-api.jpi ./github-api.jpi.old
sudo cp download *.hpi file ./
sudo chown jenkins:jenkins *.hpi 
sudo systemctl restart jenkins
login to check the version be changed


should trigger this time, how about this time
should trigger this time.
should trigger this time.

