#### Update Ubuntu

Before doing anything, you should update your server:
```
$ apt-get update && apt-get upgrade
```

#### Install PHP 7.2

  To install PHP 7.2 on Ubuntu 18.04, just run the following command:
    ```
    $ apt-get install php
    ```
    
  To verify if PHP is installed, run the following command:
  
    ```
    $ php -v
    ```
    
#### Install PHP 7.2 modules

  Run the following were *module1* *module2* etc is the name of the module seperated by space
   
    ```
    $ apt-get install module1 module2 module3
    ```

  To check all the PHP modules available in Ubuntu, run:
    
    ```
    $ apt-cache search --names-only ^php | less
    ```

    
