How to Install Jenkins on Ubuntu 24.04

sudo apt update -y && sudo apt upgrade -y

sudo apt install openjdk-21-jdk -y

java -version

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc
https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]"
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update -y

sudo apt install jenkins -y

sudo systemctl start jenkins && sudo systemctl enable jenkins

sudo apt install apache2 -y

sudo systemctl enable apache2 && sudo systemctl start apache2

sudo systemctl status apache2

touch /etc/apache2/sites-available/jenkins.conf =======> <Virtualhost *:80>
 ServerName yourdomain.com
 ProxyRequests Off
 ProxyPreserveHost On
 AllowEncodedSlashes NoDecode
 
 Order deny,allow
 Allow from all
 
 ProxyPass / http://localhost:8080/ nocanon
 ProxyPassReverse / http://localhost:8080/
 ProxyPassReverse / http://yourdomain.com/
</Virtualhost>


sudo a2ensite jenkins
sudo a2enmod headers
sudo a2enmod rewrite
sudo a2enmod proxy


cat /var/lib/jenkins/secrets/initialAdminPassword



