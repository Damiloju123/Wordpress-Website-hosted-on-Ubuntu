Step 1 - Create a directory named vagrant-vms

Command: mkdir vagrant

Step 2 - Create a directory with the name wordpress to be hosted.

Comman: mkdir wordpress

Step 3 - Change directory to the directory created in step 2

Command: cd wordpress

Step 4 - Create a vagrantfile in the wavecafe directory with the vagrant box config gotten from vagrant cloud.

Command: vagrant init ubuntu/bionic64-i

Step 5 - Use vim editor to modify the vagrantfile configuration. (this is to enable IP the address)

![network permissions](https://user-images.githubusercontent.com/52894481/184517030-ade41eb0-dcac-4080-92b4-238eb4c34c93.PNG)

Step 6 - Bring up the vm

Command: vagrant up

Step 7 - Log on to VM

Command: vagrant ssh

Step 8 - switch to root user

Command: sudo -i


Step 9 - update packages

Command: sudo apt update -y

Follow steps on Wordpress Website (https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview)

Step 10 - Start to install dependencies

Command: sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip


Step 11 - Install Wordpress, Create the installation directory and set ownership to user www-data

Command: sudo mkdir -p /srv/www

Command: sudo chown www-data: /srv/www

Command: curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www

Step 12: Configure Apache for WordPress

Enable the site with: sudo a2ensite wordpress

Enable URL rewriting with: sudo a2enmod rewrite

Disable the default “It Works” site with: sudo a2dissite 000-default

Step 13 - Reload apache to effect all the changes

Command: sudo service apache2 reload

Step 14 - To host the wordpress, there is need to create and configure a database to store data.

sudo mysql -u root

CREATE DATABASE wordpress;

CREATE USER wordpress@localhost IDENTIFIED BY '<your-password>';

GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO wordpress@localhost;

FLUSH PRIVILEGES;

quit

Step 15 - Enable MySQL

Command: sudo service mysql start

Step 16 - Configure WordPress to connect to the database

Follow the Ubuntu document.

Step 17 - Access the wordpress website with the IP Address of th VM

 ![wordpress](https://user-images.githubusercontent.com/52894481/184517042-e44ba4bf-cfb1-40b2-87f9-2e818a6413da.PNG)
