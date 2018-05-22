###### How to fix add-apt-repository command not found
  ```
  $ apt-get install python-software-properties
  ```

###### UFW massive log files
Short info:
Log files are 'rotated' by logrotate.
System specific logs are configured in ```/etc/logrotate.conf```
Other logs have config files in ```/etc/logrotate.d```

1st alternative : **edit ```/etc/logrotate.d/ufw``` to look like this**:

```
/var/log/ufw.log
{
        rotate 2
        size 200M
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog reload >/dev/null 2>&1 || true
        endscript
}
```
This it will cost you 400MB of disk space.

2st alternative2 : **No log file at all**

```
$ sudo ufw logging off
```

For more advanced options : [ufw.8 man page #Logging](http://manpages.ubuntu.com/manpages/xenial/man8/ufw.8.html#contenttoc8)

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
