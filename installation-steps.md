## Prerequisites

-   PHP 7.3+ (7.4+ suggested for 7.x.x), 8.0+ (or higher) (https://php.net)
-   MySQL 8 (or higher) (https://dev.mysql.com/downloads/mysql/8.0.html)
-   Git 2.31.1 (or higher) (https://git-scm.com)
-   Composer 2.0.14 (or higher) - for backend dependencies (https://getcomposer.org)
-   Node 16 (or higher) - for frontend dependencies (https://nodejs.org/en)

## Installation Steps

Before you start, please configure .env file with DB credentials \
(if not using docker, set DB_HOST to localhost on your dev machine)

Execute following commands for installation:

1. git checkout release_8x
2. rename ".env.example" file to ".env"
3. set DB_DATABASE, DB_USERNAME and DB_PASSWORD in the .env file
4. composer update
5. php artisan migrate
6. php artisan passport:keys
7. php artisan passport:client --password
8. php artisan passport:client --personal
9. php artisan vendor:publish --provider="Encore\Admin\AdminServiceProvider"
10. php artisan admin:install
11. php artisan Tracking APP-admin:install
12. php artisan vendor:publish --tag=api-tester

### Install from Existing Project
1. rename ".env.example" file to ".env"
2. set DB_DATABASE, DB_USERNAME and DB_PASSWORD in the .env file
3. composer update
4. php artisan vendor:publish --tag=Tracking APP-admin-assets
5. php artisan vendor:publish --tag=laravel-admin-assets

### Tracking APP Internal Packages
See internal-packages.md file for internal packages installation

### Tracking APP Public Packages
See public-packages.md file for public packages installation
