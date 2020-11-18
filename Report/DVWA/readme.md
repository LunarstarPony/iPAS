## Build DVWA Platform using CentOS 8, Nginx, PHP-FPM 7.4 and MariaDB

### Install Neccessary

#### 1, Install and enable Neccessary Repo
    sudo yum install yum-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm -y
    sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm -y
	
#### 2, Set default php version to PHP 7.4
    sudo yum module enable php:remi-7.4
	
#### 3, Install all neccessary software 
    sudo yum install php-fpm php-common php-cli php-mysqli php-gd nginx mariadb-server wget unzip -y
	
#### 4, Enable and start the software

    sudo systemctl enable mariadb nginx php-fpm.service --now
	
#### 5, Open 80 and 433 Port aand reload firewall

    sudo firewall-cmd --zone=public --add-port=433/tcp --add-port=80/tcp --permanent
	sudo firewall-cmd --reload
	
### Install Website

#### 1, Ender Nginx's default html directory 
    cd /usr/share/nginx/html/
	
#### 2, Download DVWA's file from github using wget
    sudo wget https://github.com/digininja/DVWA/archive/master.zip
	
#### 3, Delete Default index.html
    sudo rm index.html 	
	
#### 3, Unzip and copy web files
    sudo unzip master.zip; cd DVWA-master; sudo cp -r * ../; cd ..; sudo rm -r DVWA-master/; sudo rm master.zip
	
#### 4, Copy config Files
    cd config; sudo cp config.inc.php.dist config.inc.php; cd ..
	
### Configure Database

#### 1, Setup Database 
    sudo mysql_secure_installation
	
##### SQL Setup Settings
```
[lunarstarpony@DVWA html]$ sudo mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
```
#### 2, Enter MySQL Cli
    mysql -u root -p
	
#### 3, Setup a MySQL username 
    CREATE USER '{username}'@'localhost' IDENTIFIED BY '{Password}';

#### 4, Grant Permission for the new USER
    GRANT ALL PRIVILEGES ON * . * TO '{username}'@'localhost';
	
#### 5, Refresh Database 
    FLUSH PRIVILEGES;

#### 6,Config DVWA Database settings accorting to your previous settings
    sudo vi config/config.inc.php
	
##### Settings
```
$_DVWA = array();
$_DVWA[ 'db_server' ]   = 'localhost';
$_DVWA[ 'db_database' ] = 'dvwa';
$_DVWA[ 'db_user' ]     = '{Username}';
$_DVWA[ 'db_password' ] = '{Password}';
$_DVWA[ 'db_port'] = '3306';
```
#### 7, `:wq!` to save all changes

#### 8, Check yor ip address using `ip addr`

#### 9, Head into Browser and type your IP Address

#### 10, Click Create/Reset Database at the bottom of the page

#### 11, Click Login 

#### 12, Type in Default Username and Password

    Default Username: admin
	Default Password: password
	
## Success!