# Install and configure httpd webserver in RHEL8

yum install httpd mod_ssl -y && systemctl start httpd && systemctl enable httpd && mkdir /var/www/html/webserver

yum install vim wget git -y

vim /var/www/html/webserver/index.html

Write Something in this File which you want as a web page

setenforce 0

cat /etc/httpd/conf.d/myweb.conf
```
<VirtualHost *:80>
ServerAdmin  rksgoal@gmail.com
ServerName  www.singhritesh85.com
DocumentRoot  /var/www/html/webserver
DirectoryIndex  index.html
</VirtualHost>
<Directory "/var/www/html/webserver">
AllowOverride none
Require all granted
</Directory>



<VirtualHost *:443>
ServerAdmin rksgoal@gmail.com
ServerName  www.singhritesh85.com
DocumentRoot  /var/www/html/webserver
DirectoryIndex  index.html
ErrorLog  /var/log/httpd/error.log
CustomLog  /var/log/httpd/requests.log combined
SSLEngine On
SSLCertificateFile /root/nginx.crt
SSLCertificateKeyFile /root/nginx.key
</VirtualHost>
<Directory "/var/www/html/webserver">
AllowOverride none
Require all granted
</Directory>
```

systemctl restart httpd
