# multibranch-docker

#!/bin/bash

echo "STEP 1: Installing Git"
yum install git -y

echo "STEP 2: Adding Jenkins repository"
wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/rpm-stable/jenkins.repo

rpm --import \
https://pkg.jenkins.io/rpm-stable/jenkins.io-2026.key

echo "STEP 3: Installing Java 21"
yum install java-21-amazon-corretto -y

echo "Java version:"
java -version

echo "STEP 4: Installing Jenkins"
yum install jenkins -y

echo "STEP 5: Starting Jenkins"
systemctl start jenkins

echo "STEP 6: Jenkins status"
systemctl status jenkins --no-pager



yum install docker -y && systemctl start docker
chmod 777 /var/run/docker.sock


=============================================================================
Node offline issue Trouble shooting:

df -h /tmp

mount | grep ' /tmp '

sudo mount -o remount,size=2G /tmp

df -h /tmp

sudo systemctl restart Jenkins
sudo systemctl status jenkins --no-pager


