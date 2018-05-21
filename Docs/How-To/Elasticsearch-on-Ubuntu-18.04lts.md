# Install and Configure Elasticsearch on Ubuntu 18.04

## Refs: 
[Elasticsearch: Getting Started](https://www.elastic.co/webinars/getting-started-elasticsearch?baymax=rtp&elektra=products&iesrc=ctr)

[Elasticsearch Official Installation Guide](https://www.elastic.co/guide/en/elasticsearch/reference/current/_installation.html)

[Oracle JDK 8 Official Installation Guide](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

## further reading
[DigitalOcean Tutorial Step 3 — Securing Elasticsearch](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-16-04)

[Linode:How to Install and Use Elasticsearch Plugins](https://www.linode.com/docs/databases/elasticsearch/a-guide-to-elasticsearch-plugins/#elasticsearch)

## Prerequisites
### Oracle JDK 8 installed
 
### Install Java with Apt-Get on Ubuntu 18.04
    
```
$ sudo apt-get update
```
### Installing the Oracle JDK

### First, add Oracle's PPA, then update your package repository.
					
```
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
```
### Or install java 8 from ubuntu repository
Please note that headless usually refers to servers that are not connected to a monitor and don't have X11 installed
					
```
$ sudo apt install openjdk-8-jre-headless
```
					
### Setting the JAVA_HOME Environment Variable
Many programs, such as Java servers, use the JAVA_HOME environment variable to determine the Java installation location.
To set this environment variable, we will first need to find out where Java is installed.
You can do this by executing the command:
          
```
$ sudo update-alternatives --config java
````
          
Copy the path from your preferred installation and then open /etc/environment using nano or your favorite text editor.
```sudo nano /etc/environment```
							
```/etc/environment```
```JAVA_HOME="/usr/lib/jvm/java-8-oracle/jre/bin/java"```
or
```JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java"```
Save and exit the file, and reload it.
						
```
$ source /etc/environment
```
					
Test whether the environment variable has been set
						
```
echo $JAVA_HOME
```
## Install Elasticsearch
### Download the **latest** Elasticsearch version 
from [Elasticsearch Download](https://www.elastic.co/downloads/elasticsearch) 
which is 6.2.4 at the time of writing.
		
```
$ curl -L -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.2.4.deb
```
		
### Install the package the Ubuntu way with dpkg.
	
```
$ sudo dpkg -i elasticsearch-6.2.4.deb
```

Note the installation creates an **elasticsearch** group and an **elasticsearch** user.
The Elasticsearch now is installed in ```/usr/share/elasticsearch/```
with its configuration files placed in ```/etc/elasticsearch ```
and its init script added in ```/etc/init.d/elasticsearch```

### Auto Start Elasticsearch
To make sure that Elasticsearch **starts and stops automatically** with the server,
add its init script to the default runlevels run this command.
			
```
$ sudo systemctl enable elasticsearch.service
```
			
### Important: Memory size
[Setting the heap size](https://www.elastic.co/guide/en/elasticsearch/reference/current/heap-size.html)

Set the JVM heap size to approximately half of your server’s available memory.
For example, if your server has 1GB of RAM, change the Xms and Xmx values 
in the ```/etc/elasticsearch/jvm.options``` file to **512m**. 
Leave the other values in this file unchanged
		
### Start the Elasticksearch service

```
$ sudo systemctl start elasticsearch
```

