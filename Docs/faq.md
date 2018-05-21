###### How to fix add-apt-repository command not found
  ```
  $ apt-get install python-software-properties
  ```
  
###### How to change the PHP version you’re using

  If you have multiple PHP versions installed on your Ubuntu server, you can change what version is the default one.

  To set PHP 7.0 as the default, run:
    ```
    $ update-alternatives --set php /usr/bin/php7.0
    ```
  To set PHP 7.2 as the default, run:
    ```
    $ update-alternatives --set php /usr/bin/php7.2
    ```
  
  If you have installed Apache 2.4, you can configure Apache to use PHP 7.2 with the following command:
    ```
    $ a2enmod php7.2
    ```
  
  And then restart Apache for the changes to take effect:
    ```
    systemctl restart apache2
    ```
