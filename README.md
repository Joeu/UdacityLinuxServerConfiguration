# Udacity Linux Server Configuration

This project consists in the deployment of a Flask application into a Linux Server.

## Getting Started

The following instructions will get access to the server instance as a user with sudo premissions.

### IP address and SSH port

```
* IP address - http://http://18.219.137.74
* SSH Port - 2200
```

### Complete URL to access the application

```
* URL - http://ec2-18-219-137-74.us-east-2.compute.amazonaws.com
```

### Further Configuration

> Updated and upgraded the server packages

    $ sudo apt-get update
    $ sudo apt-get upgrade

> Changed ssh port from 22 to 2200.

    $ sudo nano /etc/ssh/sshd_config
    
    - Change port from 22 to 2200
    
    - Change PasswordAuthentication:
        PasswordAuthentication no
        
    - Change PermitRootLogin to:
        PermitRootLogin no
        
    - At the end of the file, add:
        AllowUsers grader  
        
    $ sudo service ssh restart

> Configured local timezone

    $ sudo dpkg-reconfigure tzdat
    
    Select 'None of the above', then select 'UTC'

> Set Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (2200), HTTP (80) and NTP (123).

    $ sudo ufw default deny incoming
    $ sudo ufw default allow outgoing
    $ sudo ufw default allow 2200/tcp
    $ sudo ufw default allow 80/tcp
    $ sudo ufw default allow 123/udp
    $ sudo ufw deny 22
    $ sudo ufw enable

>Checked running
    
    $ sudo ufw status
    
Result:

```
To                         Action      From
--                         ------      ----
22                         DENY        Anywhere
2200/tcp                   ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
123/udp                    ALLOW       Anywhere
22 (v6)                    DENY        Anywhere (v6)
2200/tcp (v6)              ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
123/udp (v6)               ALLOW       Anywhere (v6)
```

> Created user *grader* with super user permissions.

    $ sudo adduser grader
    $ sudo nano /etc/sudoers.d

> Generated SSH key pair for the newly created *grader*

    - Login into grader account:
        $ sudo su - grader
        
    Make sure you are at the /home/grader
        $ mkdir .ssh
        $ touch .ssh/authorized_keys
    
    - Local machine:
        $ ssh-keygen
        Follow the steps and copy the content of your created <file>.pub
        
    - Back to server on grader accout:
        Paste the content of the <file>.pub into .ssh/authorized_keys
        $ chmod 700 .ssh
        $ chmod 644 .ssh/authorized_keys
        $ sudo service ssh restart
    
### Summary of installed softwares

> Installed Apache

    $ sudo apt-get install apache2

> Installed PostgreSQL

    $ sudo apt-get install postgresql
    $ sudo apt-get install postgresql-contrig

> Installed Git

    $ sudo apt-get install git
    
> Other installations

    $ sudo apt-get install python-pip
    $ sudo apt-get install python-psycopg2
    $ sudo pip install virtualenv

> Packages installed with pip

```
certifi==2018.4.16
chardet==3.0.4
click==6.7
Flask==1.0.2
Flask-SeaSurf==0.2.2
Flask-SQLAlchemy==2.3.2
httplib2==0.11.3
idna==2.7
itsdangerous==0.24
Jinja2==2.10
MarkupSafe==1.0
oauth2client==4.1.2
psycopg2==2.6.1
pyasn1==0.4.4
pyasn1-modules==0.2.2
requests==2.19.1
rsa==3.4.2
six==1.11.0
SQLAlchemy==1.2.10
urllib3==1.23
virtualenv==16.0.0
Werkzeug==0.14.1
```

### Configure and Deploy application

Created the server configuration file under /etc/apache2/sites-available/<filename>.conf
Created the wsgi file on the app root folder (cloned from github)
Setup the database creating tables and schemas, running the database_setup.py and gamerecords.py
Setup Google credentials
    
### Running the application

>Restart the server and run the app

    $ sudo service apache2 restart
    $ python __init__.py

### Using the application

>With a browser of your choice, access:

    http://ec2-18-219-137-74.us-east-2.compute.amazonaws.com


* The catalog is ready to be used.
