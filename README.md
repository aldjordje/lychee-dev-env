# My development environment for the Lychee Photo Management Tool

nginx, php-fpm and mariadb docker setup with xdebug.  

## Setup
Clone this repository.
```bash
$ git clone https://github.com/aldjordje/lychee-dev-env.git
```
Copy .env.example to .env and edit environment variables.

Clone Lychee

```bash
$ git clone https://github.com/LycheeOrg/Lychee.git
```
Copy .env.example to .env and edit environment variables.

Comment on the already defined variables in this repository (DB_CONNECTION, DB_HOST, DB_PORT, DB_DATABASE, DB_USERNAME, DB_PASSWORD and LYCHEE_UPLOADS). [See an example of the Lychee .env file here.](docs/lychee.env)
## Usage

```bash
$ docker-compose up
```

### Install
```bash
$ bin/composer install
```
```bash
$ bin/artisan key:generate
```
```bash
$ bin/artisan migrate
```

### Scripts

#### Fix permissions

```bash
$ bin/artisan lychee:fix-permissions --dry-run=0
```

#### Tests

[//]: # (Currently, 362.50 MB of memory is needed to run tests, so we need to expand the memory limit.)
```bash
$ bin/phpunit -d memory_limit=512M
```

#### PHPStan

```bash
$ bin/phpstan --memory-limit=512M
```

#### PHP Coding Standards Fixer

```bash
$ bin/php-cs-fixer fix
```

### Lychee-front

Initialize the frontend submodule.
```bash
$ git submodule init
```

Get the frontend.
```bash
$ git submodule update
```

Install dependencies.
```bash
$ bin/npm install
```

#### Style formatting

```bash
$ bin/npm format
```

#### Watch for changes
While developing, you might want to use the following command to automatically build Lychee everytime you save a file:
```bash
$ bin/npm start
```