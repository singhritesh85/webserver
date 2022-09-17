# webserver
create virtual hosting for webserver


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
