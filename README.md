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
    Change port
    Change PasswordAuthentication:
        PasswordAuthentication no
    Change PermitRootLogin to:
        PermitRootLogin no
    At the end of the file, add:
        AllowUsers grader  
    $ sudo service ssh restart


* Set Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (2200), HTTP (80) and NTP (123).

> Created user *grader* with super user permissions.

    $ sudo adduser grader
    $ sudo nano /etc/sudoers.d

> Generated SSH key pair for the newly created *grader*

    Login into grader account:
        $ sudo su - grader
    Make sure you are at the /home/grader
        $ mkdir .ssh
        $ touch .ssh/authorized_keys
    
    - Local machine
        $ ssh-keygen
        Follow the steps and copy the content of your created <file>.pub
        
    - Back to server on grader accout:
        Paste the content of the <file>.pub into .ssh/authorized_keys
        $ chmod 700 .ssh
        $ chmod 644 .ssh/authorized_keys
        $ sudo service ssh restart
    
* Installed Apache

* Installed PostgreSQL

* Installed Git

### Summary of installed softwares

> Packages installed with pip

    $ pip install <package>
    
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

### Using the application

>With a browser of your choice, access:

    http://ec2-18-219-137-74.us-east-2.compute.amazonaws.com


* The catalog is ready to be used.
