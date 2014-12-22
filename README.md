# Phprest Sample Project

[![Author](http://img.shields.io/badge/author-@adammbalogh-blue.svg?style=flat-square)](https://twitter.com/adammbalogh)
[![Software License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

# Requirements

* Composer
* Php 5.4 or later
* MySql 5.x

# Installation

## 1. Create project

```cli
composer -sdev create-project phprest/phprest-sample-project /path/to/your/project
```

## 2. Create database

```cli
create database tesselboard collate=utf8mb4_unicode_ci;
```

## 3. Database migrations

*(from the root of your project dir)*

```cli
vendor/bin/phprest-service-orm migrations:migrate
```

## 4. Database fixtures

*(from the root of your project dir)*

```cli
vendor/bin/phprest-service-orm fixtures:set
```

## 5. Storage dir

Storage dir (```app/storage```) has to be writeable by the web server.

# Create Api Documentation

*(from the root of your project dir)*

```cli
vendor/bin/swagger -b public/docs/bootstrap.php -u http://localhost/docs/jsondata api/ -o public/docs/jsondata
```

## Reach your api documentation

[http://localhost/docs/index.html](http://localhost/docs/index.html)

# Api testing (spec tests)

*(from the root of your project dir)*

```cli
cd specs
npm install
cd ..
vendor/bin/phprest-service-orm fixtures:set
specs/node_modules/jasmine-node/bin/jasmine-node --verbose specs/tests
```

# Tips

* Separate your docs to an individual vhost
