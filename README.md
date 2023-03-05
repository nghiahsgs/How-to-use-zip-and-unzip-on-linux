How to install WordPress on Ubuntu Server (Ubuntu 20) using LAMP

LAMP stands for Linux, Apache, MySQL, and PHP.

Install MySQL
sql
Copy code
sudo apt-get update
sudo apt-get install mysql-server
Change root password in MySQL
sql
Copy code
sudo mysql
mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
mysql> FLUSH PRIVILEGES;
mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
Check MySQL status:

bash
Copy code
sudo /etc/init.d/mysql status
sudo /etc/init.d/mysql start
sudo /etc/init.d/mysql stop
# If MySQL is not running, activate it with "sudo systemctl start mysql"
Install phpMyAdmin
sql
Copy code
apt update && upgrade
sudo add-apt-repository universe
apt install phpmyadmin
During installation, select apache2 (use the tab and space keys to select). This means that during the phpMyAdmin creation process, you also need to install apache2 so that you can later access phpMyAdmin from your web browser.

Next, it will ask whether you want to configure the database. Click "yes" and enter the phpMyAdmin password. (Enter the same password as the root password in MySQL for speed.)

Once it's installed, try the following website to see if php is installed correctly: ip_vps/phpmyadmin/

If the phpMyAdmin login page appears, it means that you have installed it successfully.

Install some PHP libraries
When you only need to use PHP to connect to MySQL, a few libraries are sufficient, but when using WordPress, you need more.
python
Copy code
sudo apt update
sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
sudo /etc/init.d/apache2 restart
Configure Apache2 for your website and allow .htaccess Overrides and Rewrites
Here, assume that you have a domain called wp_006.com and you want to install WordPress on this domain.
Copy the default configuration file into two separate configuration files for the two websites:

bash
Copy code
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/wp_006.com.conf
Open the wp_006.com.conf file and modify it as follows:

bash
Copy code
ServerAdmin admin@wp_006.com
ServerName wp_006.com
ServerAlias www.wp_006.com
DocumentRoot /var/www/wp_006.com
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

AllowOverride All
Tip: To replace all instances of "foo" with "bar" in a file, use the following command in vim: (:%s/foo/bar/g)

Note: The Directory section allows .htaccess Overrides.

Enable 2 virtual hosts
Copy code
sudo a2ensite wp_006.com.conf
sudo service apache2 restart
sudo a2enmod rewrite
sudo service apache2 restart
The rewrite module allows WordPress to perform some functions to make post links look better.

