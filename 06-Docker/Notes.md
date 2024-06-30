What is a Container?

List of Container Vendors

Getting Started with Docker

Docker Product

Docker Architecture

Docker Installation

Docker Hub

Docker Images

Docker Networking

Docker Compose

Summary

https://docs.docker.com/

https://docs.docker.com/engine/reference/commandline/logs/

https://github.com/mmumshad/example-voting-app/tree/master

https://github.com/docker/awesome-compose
```
#!/bin/bash

# Setup Hostname 
hostnamectl set-hostname "docker.cloudbinary.io"

# Configure Hostname unto hosts file 
echo "`hostname -I | awk '{ print $1}'` `hostname`" >> /etc/hosts 

# Update the Ubuntu Local Repository with Online Repository 
sudo apt update 

# Download, Install & Configure Utility Softwares 
sudo apt install git curl unzip tree wget -y 

# Install Docker on Ubuntu Server
sudo apt-get install docker.io -y 

# Enable Docker For Ubuntu User
sudo usermod -aG docker ubuntu

# Grant Access Docker Socket
sudo chmod 777 /var/run/docker.sock

# Enable Docker Services at boot level
sudo systemctl enable docker

# Restart Docker Daemon 
sudo systemctl restart docker

```

#### Docker Commands:

```
    $ docker images

    $ docker ps 

    $ docker ps -a 

    $ docker run -d --name anyname -p 80:80 c3f279d17e0a

    $ docker exec -it container_id /bin/bash

    $ docker commit c3f279d17e0a  <Image>

    $ docker login

    $ docker images

    $ docker tag 78dcb7cc3f9f <Image>
 
    $ docker images

    $ docker push <username>/<Imagename>:<tag>
```

#### Dockerfile Examples

```

# Download Base Image from hub.docker.com
FROM ubuntu

# Execute Commands
RUN apt-get update 

# Environment Variables
ENV TZ=Asia/Kolkata   

# Update Environment Variable unto File 
RUN echo $TZ > /etc/timezone 

# Download, Install & Configure WebSever i.e. Apache - Apache2 
RUN apt-get install apache2 -y 

# Utils Package 
RUN apt-get install apache2-utils -y 

# Cleanup APT Command 
RUN apt-get clean 

# Enable WebServer Port i.e. HTTP 80/TCP
EXPOSE 80

# Execute WebServer
CMD ["apache2ctl","-D","FOREGROUND"]
```

#### Dockerfile Tomcat Example

```
# Download Base Image from hub.docker.com
FROM ubuntu

# Execute Commands
RUN apt-get update 

# Environment Variables
ENV TZ=Asia/Kolkata  

# Update Environment Variable unto File 
RUN echo $TZ > /etc/timezone 

# Download, Install & Configure 
RUN apt-get update 
RUN apt-get install openjdk-11-jdk -y 
RUN apt-get install wget -y 
RUN apt-get install curl -y 
RUN apt-get install unzip -y 

# Environment Variables
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/

# Update Environment Variable unto File 
RUN echo $JAVA_HOME >> /etc/environmen

# Cleanup APT Command 
RUN apt-get clean 

RUN mkdir /opt/tomcat/

WORKDIR /opt/
RUN curl -O https://downloads.apache.org/tomcat/tomcat-8/v8.5.87/bin/apache-tomcat-8.5.87.tar.gz
RUN cd /opt/ && tar -xzf apache-tomcat-8.5.87.tar.gz && rm apache-tomcat-8.5.87.tar.gz
RUN pwd
#RUN apache-tomcat-8.5.87.tar.gz /opt/tomcat/
RUN mv apache-tomcat-8.5.87/* /opt/tomcat/.
RUN ls -lrta /opt/tomcat/conf/tomcat-users.xml


# Take Tomcat Configuration as backup 
RUN cp /opt/tomcat/conf/tomcat-users.xml "/opt/tomcat/conf/tomcat-users.xml_$(date +%F_%R)"

# To delete last line and which contains </tomcat-users>
RUN sed -i '$d' /opt/tomcat/conf/tomcat-users.xml

#Add User & Attach Roles to Tomcat 
RUN echo '<role rolename="manager-gui"/>'  >> /opt/tomcat/conf/tomcat-users.xml
RUN echo '<role rolename="manager-script"/>' >> /opt/tomcat/conf/tomcat-users.xml
RUN echo '<role rolename="manager-jmx"/>'    >> /opt/tomcat/conf/tomcat-users.xml
RUN echo '<role rolename="manager-status"/>' >> /opt/tomcat/conf/tomcat-users.xml
RUN echo '<role rolename="admin-gui"/>'     >> /opt/tomcat/conf/tomcat-users.xml
RUN echo '<role rolename="admin-script"/>' >> /opt/tomcat/conf/tomcat-users.xml
RUN echo '<user username="admin" password="redhat@123" roles="manager-gui,manager-script,manager-jmx,manager-status,admin-gui,admin-script"/>' >> /opt/tomcat/conf/tomcat-users.xml
RUN echo "</tomcat-users>" >> /opt/tomcat/conf/tomcat-users.xml

RUN echo '<?xml version="1.0" encoding="UTF-8"?>' > /opt/tomcat/webapps/manager/META-INF/context.xml 
RUN echo '<Context antiResourceLocking="false" privileged="true" >' >> /opt/tomcat/webapps/manager/META-INF/context.xml 
RUN echo '</Context>' >> /opt/tomcat/webapps/manager/META-INF/context.xml 

RUN echo '<?xml version="1.0" encoding="UTF-8"?>' > /opt/tomcat/webapps/host-manager/META-INF/context.xml 
RUN echo '<Context antiResourceLocking="false" privileged="true" >' >> /opt/tomcat/webapps/host-manager/META-INF/context.xml 
RUN echo '</Context>' >> /opt/tomcat/webapps/host-manager/META-INF/context.xml 

WORKDIR /opt/tomcat/webapps
# RUN curl -O -L https://github.com/kesavkummari/devops/blob/master/target/devops-1.0.0-SNAPSHOT.war

COPY ./cloudops.war /opt/tomcat/webapps/

# Enable WebServer Port i.e. HTTP 80/TCP
EXPOSE 8080

# Execute WebServer
CMD ["/opt/tomcat/bin/catalina.sh", "run"]

```
#### Docker Compose - Sample Python Project

https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/django/

```
#!/bin/bash

# Setup Hostname
hostnamectl set-hostname "docker-compose.cloudbinary.io"

# Configure Hostname unto hosts file 
echo "`hostname -I | awk '{ print $1}'` `hostname`" >> /etc/hosts 

# Update Ubuntu Operating System Repository
sudo apt-get update

# Download, Install & Configure Utility Softwares 
sudo apt-get install git curl unzip tree wget -y 

# Install Docker on Ubuntu Server
sudo apt-get install docker.io -y 

# Install Docker Compose on Ubuntu 
sudo apt-get install docker-compose -y 

# Enable Docker For Ubuntu User
sudo usermod -aG docker ubuntu

# Grant Access Docker Socket
sudo chmod 777 /var/run/docker.sock

# Enable Docker Services at boot level
sudo systemctl enable docker

# Restart Docker Daemon 
sudo systemctl restart docker

```

#### Step By Step Docker Image Baking Process 
```
STEP-1: Launch an EC2 Instance of Ubuntu 

STEP-2: Install Docker & Docker-Compose

hostnamectl set-hostname "docker-compose.cloudbinary.io"
echo "`hostname -I | awk '{ print $1}'` `hostname`" >> /etc/hosts 
sudo apt-get update
sudo apt-get install git curl unzip tree wget -y 
sudo apt-get install docker.io -y 
sudo apt-get install docker-compose -y 
sudo usermod -aG docker ubuntu
sudo chmod 777 /var/run/docker.sock
sudo systemctl enable docker
sudo systemctl restart docker

STEP-3: Connect EC2 Instance using SSH/SSM 

STEP-4: Create a files using touch Dockerfile 


vi Dockerfile 
# syntax=docker/dockerfile:1
FROM python:3
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
WORKDIR /code
COPY requirements.txt /code/
RUN pip install -r requirements.txt
COPY . /code/


vi requirements.txt

Django>=3.0,<4.0
psycopg2>=2.8

vi docker-compose.yml

services:
  db:
    image: postgres
    volumes:
      - ./data/db:/var/lib/postgresql/data
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"
    environment:
      - POSTGRES_NAME=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
    depends_on:
      - db

STEP-5: Create a Django project 

$ sudo docker compose run web django-admin startproject cloudops .

STEP-6 : Change the User & Group Permissions

$ sudo chown -R $USER:$USER cloudops * 

STEP-7: Connect the database

In your project directory, edit the cloudops/settings.py file.

import os

ALLOWED_HOSTS = ['*']

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('POSTGRES_NAME'),
        'USER': os.environ.get('POSTGRES_USER'),
        'PASSWORD': os.environ.get('POSTGRES_PASSWORD'),
        'HOST': 'db',
        'PORT': 5432,
    }
}

These settings are determined by the postgres Docker image specified in docker-compose.yml.

Save and close the file.

STEP-8: Run the docker compose up command from the top level directory for your project.

$ docker-compose images
$ docker images
$ docker-compose ps
$ docker-compose up
$ docker-compose down

STEP-9: Take EC2 Instance IPaddress and Validate 

http://<ec2_instance_public_ip>


