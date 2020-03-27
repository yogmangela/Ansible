# Manualy Installing Linux Apache MySQL & PHP (LAMP Stack)

Step1: Install
```
sudo apt update
sudo apt install apache2
sudo apt install php libapache2-mod-php php-mcrypt php-mysql
sudo nano /etc/apache2/mods-enabled/dir.conf
```

```
/etc/apache2/mods-enabled/dir.conf
```
```
<IfModule mod_dir.c>
    DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>
```
change it to : copy and paste "index.php" infront
```
<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```
```
sudo systemctl restart apache2
sudo apt install php-cli
```
creating sample index.html at:
```
nano /var/www/your_domain/index.html
```
```
<html>
    <head>
        <title>Welcome to LAMP manual installation</title>
    </head>
    <body>
        <h1>Well done you have confiugured LAMP server successfully. </h1>
    </body>
</html>
```
