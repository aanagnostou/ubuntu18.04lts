##### You need to install software-properties-common to intall Php 7.1 on Ubuntu 18.04 :

```
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository ppa:ondrej/php
$ sudo add-apt-repository ppa:ondrej/apache2
$ sudo apt-get update
$ apt-get install libapache2-mod-php7.1 php7.1 php7.1-bcmath php7.1-bz2 php7.1-cgi php7.1-cli php7.1-common php7.1-curl php7.1-dba php7.1-dev php7.1-enchant php7.1-fpm php7.1-gd php7.1-gmp php7.1-imap php7.1-interbase php7.1-intl php7.1-json php7.1-ldap php7.1-mbstring php7.1-mcrypt php7.1-mysql php7.1-odbc php7.1-opcache php7.1-pgsql php7.1-phpdbg php7.1-pspell php7.1-readline php7.1-recode php7.1-snmp php7.1-soap php7.1-sqlite3 php7.1-sybase php7.1-tidy php7.1-xml php7.1-xmlrpc php7.1-xsl php7.1-zip
```

##### Case : Default PHP 7.2 is set on your system and you need to switch to PHP 7.1. 

##### Run the following commands to switch for Apache and command line.

Apache:-

```
$ sudo a2dismod php7.2
$ sudo a2enmod php7.1
$ sudo a2disconf php7.2-fpm
$ sudo a2enconf php7.1-fpm
$ sudo service apache2 restart
````

Command Line:-

```
sudo update-alternatives --set php /usr/bin/php7.1
sudo update-alternatives --set phar /usr/bin/phar7.1
sudo update-alternatives --set phar.phar /usr/bin/phar.phar7.1 
sudo update-alternatives --set phpize /usr/bin/phpize7.1
sudo update-alternatives --set php-config /usr/bin/php-config7.1
```

##### Note – The phpize7.1 and php-config7.1 command is available in php7.1-dev package.
##### This is more useful for compiling PHP modules using pecl.

##### Temp note for testing cmd:

```
$ sudo rm /usr/bin/php
$ sudo ln -s /usr/bin/php7.1 /usr/bin/php
```
