How to install WordPress on Ubuntu server (Ubuntu 20) using LAMP

LAMP is an acronym for Linux, Apache, MySQL, and PHP.

1.  Install MySQL

```
sudo apt-get update
sudo apt-get install mysql-server
```
2.  Change the root password in MySQL

sqlCopy code

```sql
sudo mysql 
mysql> SELECT user, authentication_string, plugin, host FROM mysql.user; 
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; 
mysql> FLUSH PRIVILEGES; mysql> SELECT user, authentication_string, plugin, host FROM mysql.user;
```

Check the status of MySQL

```
sudo /etc/init.d/mysql status 
sudo /etc/init.d/mysql start 
sudo /etc/init.d/mysql stop 
# If MySQL is not running, use the following command to activate it "sudo systemctl start mysql"
```
3.  Install phpMyAdmin
```
sudo apt update && upgrade
sudo add-apt-repository universe
sudo apt install phpmyadmin`
```
During the installation process, choose apache2 (use tab and space keys to select) (meaning that during the process of creating phpMyAdmin, apache2 must also be installed so that you can access phpMyAdmin from the browser later).

Next, it will ask if you want to configure the database, click yes. Enter the phpMyAdmin password (use the same password as root in MySQL for speed).

After installation, go to the following website to check if PHP has been successfully installed or not: `ip_vps/phpmyadmin/`. If the phpMyAdmin login page appears, it means you have successfully installed it.

4.  Install some PHP libraries When you only need to use PHP to connect to MySQL, just a few libraries are enough, but when you use WordPress, you need to use more.

```bash
sudo apt update
sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip restart apache
/etc/init.d/apache2 restart
```
5.  Configure Apache2 for the web and allow .htaccess Overrides and Rewrites Assuming I have the domain wp\_006.com and I want to install WordPress on this domain.

Copy the default configuration file to two separate configuration files for the two websites:

```
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/wp_006.com.conf
```
Open the `wp_006.com.conf` file and edit it as follows:

```bash
ServerAdmin admin@wp_006.com
ServerName wp_006.com
ServerAlias www.wp_006.com
DocumentRoot /var/www/wp_006.com
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

AllowOverride All
```

Note: Directory: Allows .htaccess Overrides

6.  Enable 2 virtual hosts


```bash
sudo a2ensite wp_006.com.conf
sudo service apache2 restart
sudo a2enmod rewrite
sudo service apache2 restart
```

The rewrite module allows WordPress to perform some functions that make post links look better.


7.  Download WordPress: In this guide, I will download the latest version of WordPress.

First, navigate to the tmp directory:
```
cd /tmp
```

Then, download the latest WordPress release using the `curl` command:


```
curl -O https://wordpress.org/latest.tar.gz
```

Extract the downloaded archive and move the resulting directory to `/var/www/`:

```bash
tar xzvf latest.tar.gz
touch wordpress/.htaccess
cp wordpress/wp-config-sample.php wordpress/wp-config.php
cp -r /tmp/wordpress /var/www/wp_006
```

Note: If you need to backup an existing website, you should add an `.htaccess` file with the following content inside the `wordpress` directory:

```bash
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
```

8.  Set Permissions for WordPress Files and Directories:

```bash
sudo chown -R www-data:www-data /var/www/wp_006
sudo find /var/www/wp_006 -type d -exec chmod 750 {} \;
sudo find /var/www/wp_006 -type f -exec chmod 640 {} \;
```

9.  Configure WordPress to Connect to MySQL: In the earlier step, we created a new user for MySQL connection while installing phpMyAdmin. Now, we need to use those credentials in the `wp-config.php` file.

```php
define('DB_NAME', 'wordpress');
define('DB_USER', 'wordpressuser');
define('DB_PASSWORD', 'password');
```

10.  Edit Hosts File: As we have chosen a custom domain name `wp_006.com`, we need to add this domain to the `/etc/hosts` file on your Linux machine.

bashCopy code

`sudo vi /etc/hosts`

Add the following line to the file:

Copy code

`ip_vps wp_006.com`

Note: On Windows machines, the hosts file is located at `C:\Windows\System32\drivers\etc`.

If you own the domain name, instead of modifying the `hosts` file, you can create two A records in your DNS configuration:

```bash
Host: @, Type: A, Value: IP address of your VPS
Host: a, Type: A, Value: IP address of your VPS
```

11.  Install WordPress on the Browser: Now, open your web browser and go to `wp_006.com`. You will see the WordPress installation screen as usual.

That's it! You have successfully installed WordPress on your VPS.
