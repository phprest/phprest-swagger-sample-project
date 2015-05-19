# Phprest Sample Project

[![Author](http://img.shields.io/badge/author-@adammbalogh-blue.svg?style=flat-square)](https://twitter.com/adammbalogh)
[![Software License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

# Requirements

* Composer
* Php 5.4 or latest
* MySql 5.x 

# Installation

## 1. Create project

```cli
composer -sdev create-project phprest/phprest-sample-project /path/to/your/project
```

## 2. Configure your database settings

In ```app/config/orm.php``` set your database credentials.

## 3. Create database

```cli
create database tesselboard collate=utf8mb4_unicode_ci;
```

## 4. Database migrations

*(from the root of your project dir)*

```cli
vendor/bin/phprest-service-orm migrations:migrate
```

## 5. Database fixtures

*(from the root of your project dir)*

```cli
vendor/bin/phprest-service-orm fixtures:set
```

## 6. Storage dir

*(from the root of your project dir)*

Storage dir (```app/storage```) has to be writeable by the web server.

# Create Api Documentation

*(from the root of your project dir)*

```cli
vendor/bin/swagger -b public/docs/bootstrap.php -u http://localhost/docs/jsondata api/ -o public/docs/jsondata
```

## Reach your api documentation

[http://localhost/docs/index.html](http://localhost/docs/index.html)

# List your routes

*(from the root of your project dir)*

```cli
vendor/bin/phprest routes:get
```

You should get something like this:

| Method  | Route                                   | Handler                                             |
|---------|-----------------------------------------|-----------------------------------------------------|
| OPTIONS | /{version:any}/camera                   | \Api\Camera\Controller\Camera::options              |
| GET     | /{version:any}/camera                   | \Api\Camera\Controller\Camera::get                  |
| POST    | /{version:any}/camera                   | \Api\Camera\Controller\Camera::post                 |
| GET     | /{version:any}/temperatures             | \Api\Temperature\Controller\Temperature::getAll     |
| POST    | /{version:any}/temperatures             | \Api\Temperature\Controller\Temperature::post       |
| OPTIONS | /{version:any}/temperatures             | \Api\Temperature\Controller\Temperature::optionsAll |
| OPTIONS | /{version:any}/temperatures/{id:number} | \Api\Temperature\Controller\Temperature::options    |
| GET     | /{version:any}/temperatures/{id:number} | \Api\Temperature\Controller\Temperature::get        |
| DELETE  | /{version:any}/temperatures/{id:number} | \Api\Temperature\Controller\Temperature::delete     |

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
* Use [API Blueprint](https://apiblueprint.org/) for documentation instead of Swagger
    * so you can eliminate your inner code API documentation
