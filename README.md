# Simple Docker Setup for Symfony development

## Usage

Copy .env.dist to .env and edit to suit your requirements.
`docker-compose up --build` to build the images and start up the whole cluster.
From there on a simple `docker-compose up` is all you need.
To shut it down open an second terminal and use `docker-compose down` to tear down the cluster.
To also delete all local images use `docker-compose down --rmi local`. After that you need to rebuild the images.

The html directory is a bound volume to /var/www/html in the web server image. Document root is set to /var/www/html/web.

To put in your Symfony project do a `git clone <project-url> html`, go to the html directory and call `composer install`.
When asked for the database settings use the ones defined in the `docker-compose.yml` file.

## Accessing the cluster nodes

- Webserver with PHP is under `localhost`
- phpMyAdmin runs under `localhost:8080`
- Kibana can be found under `localhost:81`

## Internals

### Installed versions

- PHP in version 7.1
- Kibana in version 4 since version 5 still has issues with running in a docker container.

### Packages installed

- vim

### PHP extensions installed

- Core
- ctype
- curl
- date
- dom
- fileinfo
- filter
- ftp
- gd
- hash
- iconv
- json
- libxml
- mbstring
- mcrypt
- mysqlnd
- mysqli
- OAuth
- openssl
- pcre
- PDO
- pdo_mysql
- pdo_pgsql
- pdo_sqlite
- pgsql
- Phar
- posix
- readline
- Reflection
- session
- SimpleXML
- soap
- SPL
- sqlite3
- standard
- tokenizer
- xdebug
- xml
- xmlreader
- xmlwriter
- yaml
- zip
- zlib
