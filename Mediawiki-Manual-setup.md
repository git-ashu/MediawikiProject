#-----------------Thought works mediawiki installation steps ubuntu 20.0 (Manually)-----------------------#

#update ubuntu 
sudo apt-get update

# Install php, mariadb, apache
sudo apt-get install apache2 mariadb-server php php-mysql libapache2-mod-php php-xml php-mbstring php-intl -y

#change directory 
cd /tmp/

#download mediawiki
sudo wget https://releases.wikimedia.org/mediawiki/1.38/mediawiki-1.38.2.tar.gz

#unzip tar 
tar -xvzf /tmp/mediawiki-*.tar.gz

#create new directory that will hold mediawiki
sudo mkdir /var/lib/mediawiki

#move contents of mediawiki to new directory
sudo mv mediawiki-*/* /var/lib/mediawiki

# create softlink to apache document root
sudo ln -s /var/lib/mediawiki /var/www/html/mediawiki

# Create LocalSettings.php from mediawiki or Place directly in mediawiki directory
#sudo cp ~/LocalSettings.php /var/www/html/mediawiki

#to access mediawiki go to > http://localhost/mediawiki


#-----------------------My SQL Setup for Mediawiki--------------------------#

#root login 
sudo mysql -u root -p 

#create user (mariadb) with password (admin)
CREATE USER 'mariadb'@'localhost' IDENTIFIED BY 'admin';

#quit from mysql
quit;

#login with maridb 
sudo mysql -u maridb -p

#create db my_wiki
CREATE DATABASE my_wiki;

#use db 
use my_wiki;

#grant permission on db to user maridb 
GRANT ALL ON my_wiki.* TO 'maridb'@'localhost';

#quit
quit;










