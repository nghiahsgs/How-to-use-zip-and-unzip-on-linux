# C-ch-c-i-wordpress-tr-n-ubuntu-server-ubuntu-20-s-d-ng-lamp
Cách cài wordpress trên ubuntu server (ubuntu 20) sử dụng lamp


<div class="entry-content" itemprop="text">

<span style="font-weight: 400;">LAMP viết tắt cho Linux, Apache, MySQL và PHP</span>

## 1\. Cài mysql

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_901340" class="syntaxhighlighter  bash">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo` `apt-get update`</div>

<div class="line number3 index2 alt2">`sudo` `apt-get` `install` `mysql-server`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

## 2\. Đổi mật khẩu cho root trong mysql

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_557152" class="syntaxhighlighter  bash">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

<div class="line number6 index5 alt1">6</div>

<div class="line number7 index6 alt2">7</div>

<div class="line number8 index7 alt1">8</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo` `mysql`</div>

<div class="line number2 index1 alt1">`mysql > SELECT user,authentication_string,plugin,host FROM mysql.user;`</div>

<div class="line number4 index3 alt1">`mysql > ALTER USER` `'root'``@``'localhost'` `IDENTIFIED WITH mysql_native_password BY` `'password'``;`</div>

<div class="line number6 index5 alt1">`mysql > FLUSH PRIVILEGES;`</div>

<div class="line number8 index7 alt1">`mysql > SELECT user,authentication_string,plugin,host FROM mysql.user;`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

<span style="font-weight: 400;">Xem status của mysql</span>

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_41800" class="syntaxhighlighter  bash">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo` `/etc/init``.d``/mysql` `status`</div>

<div class="line number2 index1 alt1">`sudo` `/etc/init``.d``/mysql` `start`</div>

<div class="line number3 index2 alt2">`sudo` `/etc/init``.d``/mysql` `stop`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

<span style="font-weight: 400;"># nếu mysql chưa chạy thì dùng câu lệnh sau để kích hoạt “sudo systemctl start mysql”</span>

## 3.Cài php myadmin

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_570134" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`apt update && upgrade`</div>

<div class="line number3 index2 alt2">`sudo add-apt-repository universe`</div>

<div class="line number5 index4 alt2">`apt install phpmyadmin`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

<span style="font-weight: 400;">Trong quá trình cài đặt, hãy chọn apache2 (dùng phím tab và space để chọn) (tức là trong quá trình tạo phpmyadmin thì cũng cần cài luôn apache2 để sau này các bạn truy cập phpmyadmin từ trình duyệt)</span>

<span style="font-weight: 400;">Tiếp theo nó hỏi có muốn cấu hình database không, thì bấm vào có. Điền pass phpmyadmin vào</span>

<span style="font-weight: 400;">(Điền luôn pass giống của root trong mysql cho nhanh)</span>

<span style="font-weight: 400;">Cài xong vào thử trang web sau để xem php cài thành công hay chưa : ip_vps/phpmyadmin/</span>

<span style="font-weight: 400;">Nếu nó hiện ra trang đăng nhập phpmyadmin nghĩa là bạn đã cài đặt thành công</span>

## 4\. Cài một số thư viện php

<span style="font-weight: 400;">Khi bạn chỉ cần dùng php kết nối với mysql thì chỉ cần vài thư viện là đủ, nhưng khi bạn dùng wordpress, bạn cần dùng nhiều hơn</span>

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_552619" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

<div class="line number6 index5 alt1">6</div>

<div class="line number7 index6 alt2">7</div>

<div class="line number8 index7 alt1">8</div>

<div class="line number9 index8 alt2">9</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo apt update`</div>

<div class="line number3 index2 alt2">`sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip`</div>

<div class="line number7 index6 alt2">`restart apache`</div>

<div class="line number9 index8 alt2">`/etc/init.d/apache2 restart`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

## 5\. Cài đặt cấu hình apache2 cho web và cho phép .htaccess Overrides và Rewrites

**Ở đây giả sử tôi có tên miền wp_006.com và tôi muốn cài wordpress lên tên miền này.**

<span style="font-weight: 400;">copy file cấu hình default ra thành 2 file cấu hình riêng cho 2 web</span>

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_861563" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/wp_006.com.conf`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

<span style="font-weight: 400;">Mở file wp_006.com.conf sửa nó thành như sau</span>

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_698288" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

<div class="line number6 index5 alt1">6</div>

<div class="line number7 index6 alt2">7</div>

<div class="line number8 index7 alt1">8</div>

<div class="line number9 index8 alt2">9</div>

<div class="line number10 index9 alt1">10</div>

<div class="line number11 index10 alt2">11</div>

<div class="line number12 index11 alt1">12</div>

<div class="line number13 index12 alt2">13</div>

<div class="line number14 index13 alt1">14</div>

<div class="line number15 index14 alt2">15</div>

<div class="line number16 index15 alt1">16</div>

<div class="line number17 index16 alt2">17</div>

<div class="line number18 index17 alt1">18</div>

<div class="line number19 index18 alt2">19</div>

<div class="line number20 index19 alt1">20</div>

<div class="line number21 index20 alt2">21</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`<VirtualHost *:80>`</div>

<div class="line number3 index2 alt2">`ServerAdmin admin@wp_006.com`</div>

<div class="line number5 index4 alt2">`ServerName wp_006.com`</div>

<div class="line number7 index6 alt2">`ServerAlias www.wp_006.com`</div>

<div class="line number9 index8 alt2">`DocumentRoot /var/www/wp_006.com`</div>

<div class="line number11 index10 alt2">`ErrorLog ${APACHE_LOG_DIR}/error.log`</div>

<div class="line number13 index12 alt2">`CustomLog ${APACHE_LOG_DIR}/access.log combined`</div>

<div class="line number15 index14 alt2">`</VirtualHost>`</div>

<div class="line number17 index16 alt2">`<Directory /var/www/wp_006/>`</div>

<div class="line number19 index18 alt2">`AllowOverride All`</div>

<div class="line number21 index20 alt2">`</Directory>`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

<span style="font-weight: 400;">tip: để replace tất cả ký tự foo thành bar trong file, dùng câu lệnh sau trong vim (:%s/foo/bar/g)</span>

ghi chu : Directory : cho phép .htaccess Overrides

## <span style="font-weight: 400;">6\. Enable 2 virtual hosts</span>

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_784791" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

<div class="line number6 index5 alt1">6</div>

<div class="line number7 index6 alt2">7</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo a2ensite wp_006.com.conf`</div>

<div class="line number3 index2 alt2">`sudo service apache2 restart`</div>

<div class="line number5 index4 alt2">`sudo a2enmod rewrite`</div>

<div class="line number7 index6 alt2">`sudo service apache2 restart`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

<span style="font-weight: 400;">module rewrite cho phép wp thực hiện 1 số chức năng làm link post đẹp hơn</span>

## 7\. Download wordpress

<span style="font-weight: 400;">Ở hướng dẫn này, tôi sẽ download bản mới nhất của wp về</span>

<span style="font-weight: 400;">cd /tmp</span>

<span style="font-weight: 400;">curl -O https://wordpress.org/latest.tar.gz</span>

<span style="font-weight: 400;">giải nén file tar ra được 1 thư mục tên là wordpress</span>

<span style="font-weight: 400;">tar xzvf latest.tar.gz</span>

<span style="font-weight: 400;">trong thư mục wordpress tạo file .htaccess</span>

<span style="font-weight: 400;">touch .htaccess</span>

<span style="font-weight: 400;">copy file config mẫu của wp sang file config của wp</span>

<span style="font-weight: 400;">cp wp-config-sample.php wp-config.php</span>

<span style="font-weight: 400;">copy cả thư mục wordpress trong tmp sang var/www</span>

<span style="font-weight: 400;">cp -r /tmp/wordpress /var/www/wp_006</span>

Tips: Trong truong hop ban can backup website (bai nay huong dan tao moi web wp) ban hay them file htaccess trong thu muc wordpress voi noi dung nhu sau:

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_856293" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

<div class="line number6 index5 alt1">6</div>

<div class="line number7 index6 alt2">7</div>

<div class="line number8 index7 alt1">8</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`<IfModule mod_rewrite.c>`</div>

<div class="line number2 index1 alt1">`RewriteEngine On`</div>

<div class="line number3 index2 alt2">`RewriteBase /`</div>

<div class="line number4 index3 alt1">`RewriteRule ^index\.php$ - [L]`</div>

<div class="line number5 index4 alt2">`RewriteCond %{REQUEST_FILENAME} !-f`</div>

<div class="line number6 index5 alt1">`RewriteCond %{REQUEST_FILENAME} !-d`</div>

<div class="line number7 index6 alt2">`RewriteRule . /index.php [L]`</div>

<div class="line number8 index7 alt1">`</IfModule>`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

## 8\. Chỉnh quyền cho các file và các thư mục trong wp

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_574373" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`sudo chown -R www-data:www-data /var/www/wp_006.com`</div>

<div class="line number3 index2 alt2">`sudo find /var/www/wp_006.com/ -type d -exec chmod 750 {} \;`</div>

<div class="line number5 index4 alt2">`sudo find /var/www/wp_006.com/ -type f -exec chmod 640 {} \;`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

## 9\. Chỉnh file cấu hình wp kết nối với mysql

<span style="font-weight: 400;">Ở bước cài phpmyadmin, chúng ta đã tạo được 1 user để kết nối với mysql. Bây giờ chúng ta cần ghi các thông tin đó vào file wp-config.php</span>

<div class="wp-block-syntaxhighlighter-code ">

<div>

<div id="highlighter_303874" class="syntaxhighlighter  plain">

<table border="0" cellpadding="0" cellspacing="0">

<tbody>

<tr>

<td class="gutter">

<div class="line number1 index0 alt2">1</div>

<div class="line number2 index1 alt1">2</div>

<div class="line number3 index2 alt2">3</div>

<div class="line number4 index3 alt1">4</div>

<div class="line number5 index4 alt2">5</div>

<div class="line number6 index5 alt1">6</div>

<div class="line number7 index6 alt2">7</div>

<div class="line number8 index7 alt1">8</div>

<div class="line number9 index8 alt2">9</div>

<div class="line number10 index9 alt1">10</div>

<div class="line number11 index10 alt2">11</div>

<div class="line number12 index11 alt1">12</div>

<div class="line number13 index12 alt2">13</div>

</td>

<td class="code">

<div class="container">

<div class="line number1 index0 alt2">`define( 'DB_NAME', 'wordpress' );`</div>

<div class="line number5 index4 alt2">`/ MySQL database username */`</div>

<div class="line number7 index6 alt2">`define( 'DB_USER', 'wordpressuser' );`</div>

<div class="line number11 index10 alt2">`/ MySQL database password */`</div>

<div class="line number13 index12 alt2">`define( 'DB_PASSWORD', 'password' );`</div>

</div>

</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

## <span style="font-weight: 400;">10\. Sửa file hosts trên máy của bạn</span>

<span style="font-weight: 400;">Vì wp_006.com tên miền mình tưởng tượng ra chứ mình đâu có sở hữu</span>

<span style="font-weight: 400;">Vì vậy cần sửa file hosts trên máy linux của bạn</span>

<span style="font-weight: 400;">sudo vi /etc/hosts</span>

Trên windows là C:\Windows\System32\drivers\etc

<span style="font-weight: 400;">Thêm dòng sau vào</span>

<span style="font-weight: 400;">ip_vps wp_006.com</span>

<span style="font-weight: 400;">Bây giờ bạn vào chrome và mở wp_006.com và xem kết quả</span>

<span style="font-weight: 400;">Bonus: nếu bạn sở hữu tên miền, hãy trỏ nó về vps thay vì mở file hosts và sửa như trên</span>

<span style="font-weight: 400;">Mở dns và thêm 2 record</span>

<span style="font-weight: 400;">Host : @ , loại A, giá trị là ip của vps</span>

<span style="font-weight: 400;">Host : a , loại A, giá trị là ip của vps</span>

## 11.Cài đặt trên browser

<span style="font-weight: 400;">Bây giờ các bạn mở trình duyệt, truy cập vào wp_006.com, sẽ hiện ra cài đặt wp như bình thường</span>

</div>
