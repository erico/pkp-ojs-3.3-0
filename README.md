LAMP stack built with Docker Compose to use with PKP-OJS. latest version.
Many thanks to repositories, as follows:
Lamp Stack - https://github.com/sprintcube. SprintCube is a digital product design & development agency working with startups, businesses to help them build better products, faster. Thanks for their work in https://github.com/sprintcube/docker-compose-lamp
PKP-OJS - https://github.com/pkp - Public Knowledge Project. This is the official Github account for PKP. We track most software milestones in the pkp-lib repository (pinned below).

To make both meet our needs, some modifications have been made. Feel free to change ou branch the repository.

1 - Lamp Stack - a basic LAMP stack environment built using Docker Compose. It consists of the following:

* PHP 7.4
* Apache 2.4
* PostgreSQL 12.1
* Redis 6.0.8

##  Installation
 
* Clone this repository on your local computer
* configure .env as needed 
* Run the `docker-compose up -d`.

```shell
git clone https://github.com/erico/pkp-ojs-3.3-0
cd docker-compose-lamp/
cp ehg.env .env
// modify sample.env as needed
docker-compose up -d
// visit localhost
```

Your LAMP stack is now ready!! You can access it via `http://localhost`.

##  Configuration and Usage

### General Information 
This Docker Stack is build for local development and not for production usage.

### Configuration
This package comes with default configuration options. You can modify them by creating `.env` file in your root directory.
To make it easy, just copy the content from `sample.env` file and update the environment variable values as per your need.

### Configuration Variables
There are following configuration variables available and you can customize them by overwritting in your own `.env` file.

---
#### PHP
---
_**PHPVERSION**_
Is used to specify which PHP Version you want to use. Defaults always to latest PHP Version. 

_**PHP_INI**_
Define your custom `php.ini` modification to meet your requirments. 

---
#### Apache 
---

_**DOCUMENT_ROOT**_

It is a document root for Apache server. The default value for this is `./www`. All your sites will go here and will be synced automatically.

_**VHOSTS_DIR**_

This is for virtual hosts. The default value for this is `./config/vhosts`. You can place your virtual hosts conf files here.

> Make sure you add an entry to your system's `hosts` file for each virtual host.

_**APACHE_LOG_DIR**_

This will be used to store Apache logs. The default value for this is `./logs/apache2`.

---
#### Database
---

_**DATABASE**_
Define PostgreSQL . 

_**POSTGRESQL_DATA_DIR**_

This is PostgreSQL data directory. The default value for this is `./data/pgsql`. All your PostgreSQL data files will be stored here.

_**POSTGRESQL_LOG_DIR**_

This will be used to store Apache logs. The default value for this is `./logs/pgsql`.

## Web Server

Apache is configured to run on port 80. So, you can access it via `http://localhost`.

#### Apache Modules

By default following modules are enabled.

* rewrite
* headers

> If you want to enable more modules, just update `./bin/webserver/Dockerfile`. You can also generate a PR and we will merge if seems good for general purpose.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.

#### Connect via SSH

You can connect to web server using `docker-compose exec` command to perform various operation on it. Use below command to login to container via ssh.

```shell
docker-compose exec webserver bash
```

## PHP

The installed version of depends on your `.env`file. 

#### Extensions

By default following extensions are installed. 
May differ for PHP Verions <7.x.x

* mysqli
* pdo_sqlite
* pdo_mysql
* pdo_pgsql
* mbstring
* zip
* intl
* mcrypt
* curl
* json
* iconv
* xml
* xmlrpc
* gd

> If you want to install more extension, just update `./bin/webserver/Dockerfile`. You can also generate a PR and we will merge if it seems good for general purpose.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.

## phpMyAdmin

phpMyAdmin is configured to run on port 8080. Use following default credentials.

http://localhost:8080/  
username: root  
password: ehgr00t

## Redis

It comes with Redis. It runs on default port `6379`.

## Contributing
>We are happy if you want to create a pull request or help people with their issues. If you want to create a PR, please remember that this stack is not built for production usage, and changes should good for general purpose and not overspecialized. 
>Please note that we simplified the project structure from several branches for each php version, to one centralized master branch.  Please create your PR against master branch. 
 
Thank you! 


# pkp-ojs-3.3-0
