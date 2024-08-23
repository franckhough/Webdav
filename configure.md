https://reintech.io/blog/configuring-webdav-server-rocky-linux-9

mkdir /var/www/html/webdav
chown -R apache:apache /var/www/html/webdav

nano /etc/httpd/conf.d/webdav.conf

Add the following section into the webdav.conf file:

  <Directory "/var/www/html/webdav">
    DAV On
    AuthType Basic
    AuthName "WebDAV"
    AuthUserFile /etc/httpd/webdav.password
    Require valid-user
  </Directory>

htpasswd -c /etc/httpd/webdav.password your_username

chmod 640 /etc/httpd/webdav.password
chown root:apache /etc/httpd/webdav.password

Now start or restart the httpd service.
