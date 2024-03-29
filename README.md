# What is LNMP one-click installation package?

  LNMP one-click installation package is a can be written in Linux shells for CentOS/RadHat/Fedora, Debian/Ubuntu/Raspbian/Deepin Linux VPS or independent host installed LNMP (Nginx/MySQL/PHP),
  LNMPA (Nginx/MySQL/PHP/Apache), LAMP (Apache/MySQL/PHP) Shell program production environment. At the same time provide some practical tools such as: virtual host management, FTP user management, Nginx, MySQL/MariaDB, PHP upgrades, common cache component installation, reset the MySQL root password, 502 automatic restart protective DenyHosts, log cutting, SSH/Fail2Ban, backup, and many other useful scripts.

  LNMP website：https://lnmp.org
  Emial to : shaonbean@qq.com
#System requirements:

  CentOS/RHEL/Fedora/Debian/Ubuntu/Raspbian Linux system

  Need more than 5 gb hard disk space left

  Need more than 128 MB of memory (if the small memory is 128 MB VPS, Xen requires a SWAP, should have at least 128 MB of OpenVZ more vSWAP or sudden memory), pay attention to the small memory, do not use a 64 - bit system.

  To install MySQL 5.6 or 5.7 and MariaDB 10 must be more than 1 g memory!.

  VPS or server, it must have been connected to the Internet and you must set up the network source can't be a CD source, at the same time VPS/DNS server to normal!

  Under Linux case-sensitive, when entering the command, please note!

# Installation

  Before installation it is recommended to use screen, perform: screen -s lnmp,Then use the following command:perform

  wget -c http://soft.vpser.net/lnmp/lnmp1.3-full.tar.gz && tar zxf lnmp1.3-full.tar.gz && cd lnmp1.3-full && ./install.sh {lnmp|lnmpa|lamp}

  Such as bolt can use screen -r LNMP recovery.
  Detailed installation tutorial reference: https://lnmp.org/install.html

  Note: this version added LNMP conf configuration file, you can customize to download the address of the server, the database directory and nginx and compile PHP parameters, no matter the installation upgrade will invoke the file set, can install or upgrade
  Follow up demand changes.

# Commonly used functions

  The following carry out, LNMP directory for the default for lnmp1.3 - full or lnmp1.3, can customize the name of the other

1. Installl FTP Server

  perform：./pureftpd.sh install,Can use lnmp ftp {add|list|del} manage ftp.

  The upgrade script

  perform: ./upgrade.sh   #According to the prompt to choose
  Also can use directly parameters: ./upgrade.sh {nginx|mysql|mariadb|php|phpa|m2m|phpmyadmin}

2. Parameter meaning

  1. nginx             # Can be upgraded to any Nginx version.
  2. mysql             # Can be upgraded to any MySQL version, the MySQL upgrade risk is bigger, although will automatically backup data, still suggest to backup again.
  3. mariadb           # Can upgrade installed Mariadb, although will automatically backup data, still suggest to backup again.
  4. m2m               # Can upgrade to Mariadb from MySQL, although will automatically backup data, still suggest to backup again.
  5. php               # Applies only to LNMP, most can be upgraded to PHP version.
  6. phpa              # Can upgrade LNMPA/to most PHP version of the LAMP.
  7. phpmyadmin        # Can upgrade phpMyadmin。

3. extensions

  perform: ./addons.sh {install|uninstall} {eaccelerator|xcache|memcached|opcache|redis|imagemagick|ioncube}

  Cache acceleration:

    1. xcache            # When installation should choose version and a password,through http://yourIP/xcache/ manage. Username: admin, Password you can set when install xcache.
    2. redis
    3. memcached         # Can choose the PHP memcache or PHP - memcached extension.
    4. opcache           # Manage website: http://yourIP/ocp.php.
    5. eaccelerator
    NOTE: Please do not install multiple cache class extension module, multiple problems may lead to web site!

4. Image processing

  perform: ./addons.sh {install|uninstall} imageMagick imageMagick
  Path: /usr/local/imagemagick/bin/

5. Decryption

  perform: ./addons.sh {install|uninstall} ionCube.

  Other:

   1. perform: ./php5.2.17.sh  # Install a don't conflict with LNMP PHP 5.2.17 exist alone, directory in/usr/local/php52 /, when using need to nginx virtual host configuration text > a PHP - cgi. The sock is modified to PHP - cgi52. Can call PHP5.2.17 sock. 
--   The following tools in LNMP installation package tools directory
   2. perform：./reset_mysql_root_password.sh # Reset MySQL/MariaDB root password.
   3. perform：./check502.sh                  # Can detect whether PHP - FPM hang up, 502 error when restart, cooperate to use crontab 
   4. perform：./cut_nginx_logs.sh            # Log cutting script.
   5. perform：./remove_disable_function.sh   # Run this script to disable the function can be deleted.

6. Uninstall

  Uninstall LNMP、LNMPA or LAMP, perform：./uninstall.sh Select uninstall according to directions.

7. State management

  LNMP/LNMPA/LMAP State management：lnmp {start|stop|reload|restart|kill|status}

  1. Nginx State management：lnmp nginx or /etc/init.d/nginx {start|stop|reload|restart}
  2. MySQL State management：lnmp mysql or /etc/init.d/mysql {start|stop|restart|reload|force-reload|status}
  3. MariaDB State management：lnmp mariadb or /etc/init.d/mariadb {start|stop|restart|reload|force-reload|status}
  4. PHP-FPM State management：lnmp php-fpm or /etc/init.d/php-fpm {start|stop|quit|restart|reload|logrotate}
  5. PureFTPd State management：lnmp pureftpd or /etc/init.d/pureftpd {start|stop|restart|kill|status}
  6. Apache State management：lnmp httpd or /etc/init.d/httpd {start|stop|restart|graceful|graceful-stop|configtest|status}

8. Virtual host management

  ADD：lnmp vhost add
  DELETE：lnmp vhost del
  LIST：lnmp vhost list

9. Related to the graphical interface

  1. PHPMyAdmin：http://yourIP/phpmyadmin/
  2. phpinfo：http://yourIP/phpinfo.php
  3. PHP probe：http://yourIP/p.php
  4. Xcache Management interface：http://yourIP/xcache/
  5. Zend Opcache Management interface：http://yourIP/ocp.php

# LNMP related catalog file

1. Directory location

  Nginx：/usr/local/nginx/
  MySQL：/usr/local/mysql/
  MariaDB：/usr/local/mariadb/
  PHP：/usr/local/php/
  PHPMyAdmin：/home/wwwroot/default/phpmyadmin/
  The default virtual host site directory: /home/wwwroot/default/
  Nginx log path：/home/wwwlogs/

  Nginx configuration file：/usr/local/nginx/conf/nginx.conf
  MySQL/MariaDB configuration file：/etc/my.cnf
  PHP configuration file：/usr/local/php/etc/php.ini
  PHP-FPM configuration file：/usr/local/php/etc/php-fpm.conf
  PureFtpd configuration file：/usr/local/pureftpd/etc/pure-ftpd.conf
  Apache configuration file：/usr/local/apache/conf/httpd.conf


# Technical support

  Technical support BBS: http://bbs.vpser.net/forum-25-1.html

# NOTE

  If you git clone this project to your local,Please download and install LNMP required source package.Download are necessary package to LNMP SRC subdirectory of the directory
 
  Download address: http://soft.vpser.net 
  
