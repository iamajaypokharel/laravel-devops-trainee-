### Laravel implementation of RealWorld app

This Laravel app is part of the [RealWorld](https://github.com/gothinkster/realworld) project and implementation of the [Laravel best practices](https://github.com/alexeymezenin/laravel-best-practices).

You might also check [Ruby on Rails version](https://github.com/alexeymezenin/ruby-on-rails-realworld-example-app) of this app.

See how the exact same Medium.com clone (called [Conduit](https://demo.realworld.io)) is built using different [frontends](https://codebase.show/projects/realworld?category=frontend) and [backends](https://codebase.show/projects/realworld?category=backend). Yes, you can mix and match them, because **they all adhere to the same [API spec](https://gothinkster.github.io/realworld/docs/specs/backend-specs/introduction)**

### How to run the API

Make sure you have PHP and Composer installed globally on your computer.

Clone the repo and enter the project folder

```
git clone https://github.com/alexeymezenin/laravel-realworld-example-app.git
cd laravel-realworld-example-app
```

Install the app

```
composer install
cp .env.example .env
```

Run the web server

```
php artisan serve
```

That's it. Now you can use the api, i.e.

```
http://127.0.0.1:8000/api/articles
```


from ajayman
Laravel DevOps Beginner Guide (Up to artisan serve)
This guide explains how to clone a Laravel project, install PHP, Composer, SQLite, configure the application, and run it using the built-in Laravel development server. It also shows how to access it via an EC2 public IP.

1. Prerequisites
•	Ubuntu server (local VM or EC2)
•	Git installed
•	Internet connection
•	Security Group allows TCP 8000 (EC2)
2. Clone Repository
git clone https://github.com/iamajaypokharel/laravel-devops-trainee-.git
cd laravel-devops-trainee-
3. Install PHP and Extensions
sudo apt update
sudo apt install -y php php-cli php-fpm php-sqlite3 php-xml php-mbstring php-curl php-zip php-bcmath php-gd unzip git sqlite3
4. Install Composer
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
composer --version
5. Install Dependencies
composer install
Purpose: Downloads all PHP packages listed in composer.json into the vendor directory.
6. Configure Environment
cp .env.example .env
php artisan key:generate
Edit .env:
DB_CONNECTION=sqlite
touch database/database.sqlite
7. Run Migrations
php artisan migrate
8. Start Laravel
php artisan serve --host=0.0.0.0 --port=8000
Using --host=0.0.0.0 allows connections from other machines instead of only localhost.
9. Access from Browser
Local: http://127.0.0.1:8000
EC2: http://<EC2-PUBLIC-IP>:8000
Example API endpoint if your application defines routes in routes/api.php:
http://<EC2-PUBLIC-IP>:8000/api/users  or if you want you can /api/articles for backend 
Replace /api/users with your actual API route.
10. Troubleshooting
•	vendor/autoload.php missing: Run composer install
•	Application key missing: php artisan key:generate
•	SQLite error: touch database/database.sqlite and set DB_CONNECTION=sqlite
•	Port 8000 not reachable: Open inbound TCP 8000 in EC2 Security Group and use --host=0.0.0.0



