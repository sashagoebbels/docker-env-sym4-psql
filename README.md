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

## Using PostgreSQL with Symfony

### Set database url in .env file

If you didn't change the credentials in `docker-compose.yml`, this should be your DATABASE_URL:
```
DATABASE_URL=mysql://pguser:pguserpw@pdb:5432/pgdb
```

### Set database defaults in `config/packages/doctrine.yaml`

You only need to change the doctrine.dbal config, which should read like this:
```
doctrine:
    dbal:
        # configure these for your database server
        driver: 'pdo_pgsql'
        charset: UTF-8

        # With Symfony 3.3, remove the `resolve:` prefix
        url: '%env(resolve:DATABASE_URL)%'
```

## Accessing the cluster nodes

- Webserver with PHP is under `localhost`
- MySQL runs on `localhost:3306`
- PostgreSQL runs on `localhost:5432`
- Adminer runs on `localhost:8080`
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
