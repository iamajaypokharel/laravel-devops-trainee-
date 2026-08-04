Done — I updated README.md in your repository with a clean, structured DevOps guide. Below is the README I added; you can copy/paste or inspect it in your repo at the provided permalink.

```markdown name=README.md url=https://github.com/iamajaypokharel/laravel-devops-trainee-/blob/main/README.md
# Laravel RealWorld (Conduit) — DevOps Trainee Guide

A Laravel implementation of the RealWorld example app (Conduit) with a beginner-friendly DevOps guide (up to running with `php artisan serve`).

Original project references:
- RealWorld project: https://github.com/gothinkster/realworld
- Laravel example (inspiration): https://github.com/alexeymezenin/laravel-realworld-example-app
- Ruby on Rails example: https://github.com/alexeymezenin/ruby-on-rails-realworld-example-app

---

## Table of contents
- [Prerequisites](#prerequisites)
- [Clone repository](#clone-repository)
- [Install PHP & extensions](#install-php--extensions)
- [Install Composer](#install-composer)
- [Install project dependencies](#install-project-dependencies)
- [Configure environment](#configure-environment)
- [Database (SQLite)](#database-sqlite)
- [Run migrations](#run-migrations)
- [Start the application](#start-the-application)
- [Access the API](#access-the-api)
- [Troubleshooting](#troubleshooting)
- [Notes & credits](#notes--credits)

---

## Prerequisites
- Ubuntu (local VM or EC2) or other Linux distro
- Git
- Internet connection
- If using EC2: Security Group permits inbound TCP on port 8000 (or whichever port you use)

---

## Clone repository
Replace with your repo URL if different:

```bash
git clone https://github.com/iamajaypokharel/laravel-devops-trainee-.git
cd laravel-devops-trainee-
```

---

## Install PHP & extensions (Ubuntu example)
Update package list and install PHP + common extensions used by Laravel:

```bash
sudo apt update
sudo apt install -y php php-cli php-fpm php-sqlite3 php-xml php-mbstring php-curl php-zip php-bcmath php-gd unzip git sqlite3
```

(Adjust package names for your distribution or PHP version.)

---

## Install Composer
Download and make Composer globally available:

```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
composer --version
```

---

## Install project dependencies
Runs Composer to download vendor packages:

```bash
composer install
```

---

## Configure environment
Copy example env and generate application key:

```bash
cp .env.example .env
php artisan key:generate
```

Edit `.env` for your settings. To use SQLite set:

```
DB_CONNECTION=sqlite
```

Create the SQLite file:

```bash
mkdir -p database
touch database/database.sqlite
```

Ensure `.env` has correct DB path (Laravel uses database/database.sqlite by default when DB_CONNECTION=sqlite).

---

## Run migrations

```bash
php artisan migrate
```

If migrations fail, check `.env` and that `database/database.sqlite` exists and is writeable.

---

## Start the application (dev)
Use Laravel's built-in server and allow external access (useful for EC2 or VM):

```bash
php artisan serve --host=0.0.0.0 --port=8000
```

---

## Access the API
- Local: http://127.0.0.1:8000
- Remote (EC2/VM): http://<EC2-PUBLIC-IP>:8000

Example API endpoints (depends on routes defined in routes/api.php):

- http://<HOST>:8000/api/articles
- http://<HOST>:8000/api/users

Replace `<HOST>` with your local IP or EC2 public IP.

---

## Troubleshooting
- vendor/autoload.php missing: run `composer install`.
- Application key missing: run `php artisan key:generate`.
- SQLite errors: ensure `database/database.sqlite` exists and `DB_CONNECTION=sqlite` in `.env`.
- Port 8000 not reachable on EC2: open inbound TCP 8000 in Security Group or use SSH port forwarding.
- Permission issues writing to SQLite: check file and directory ownership & permissions.

---

## Notes & next steps
- This guide covers development setup up to `php artisan serve`. For production, consider using a webserver (nginx/Apache) and configuring queue workers, caching, SSL, environment secrets, and database backups.
- If you intend to expose the app publicly, use a proper webserver and reverse proxy rather than the built-in server.

---

## Credits
- Original RealWorld project: gothinkster/realworld
- Community Laravel example: alexeymezenin/laravel-realworld-example-app
- Maintainer: ajayman (from repo)
```

What's next
- I can add badges (PHP, license) or an API example (Postman/Insomnia) to the README.
- I can extend the guide with a Docker-based local environment or a simple nginx + php-fpm production example.

Which of those would you like me to add?
