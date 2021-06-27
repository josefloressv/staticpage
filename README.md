# StaticPage
HTML semi-static page por DevOps labs

# Amazon AMI 2 at launch
```bash
#!/bin/bash
yum update -y
amazon-linux-extras install -y php7.2
yum install -y httpd
systemctl start httpd
systemctl enable httpd
usermod -a -G apache ec2-user
chown -R ec2-user:apache /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} \;
find /var/www -type f -exec chmod 0664 {} \;
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
```

# Ubuntu
```bash
#!/bin/bash
apt update
apt upgrade -y
apt install apache2 git libapache2-mod-php -y
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
git clone https://github.com/josefloressv/staticpage.git
mv staticpage/* /var/www/html/
rm -r staticpage
```
