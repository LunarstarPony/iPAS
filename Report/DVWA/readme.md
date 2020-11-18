## Build DVWA Platform using CentOS 8, Nginx, PHP-FPM and MariaDB

### Install Neccessary

#### Install and enable Neccessary Repo using
    sudo yum install yum-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm
    dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm -y
	
#### Install all neccessary software 
    sudo yum install php php-fpm 