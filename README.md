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
### Summary of installed softwares

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

### Further Configuration

* Changed ssh port from 22 to 2200.

* Set Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (2200), HTTP (80) and NTP (123).

* Created user *grader* with super user permissions.

* Generated SSH key pair for the newly created *grader*

* Updated and upgraded the server packages

* Installed Apache

* Installed PostgreSQL

* Installed Git

### Using the application

>With a browser of your choice, access:

    http://ec2-18-219-137-74.us-east-2.compute.amazonaws.com


* The catalog is ready to be used.
