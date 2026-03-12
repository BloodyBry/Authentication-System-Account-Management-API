# Authentication System & Account Management API

## Project Overview

This project is a RESTful API built with Laravel that provides a complete authentication and account management system.

The API allows users to:
- Create an account
- Log in and receive an authentication token
- Access protected routes
- Update their profile
- Change their password
- Log out
- Delete their account

Authentication is implemented using **Laravel Sanctum** with token-based authentication.

The API is designed to be tested only through **Postman** (no frontend interface).

---

# Technologies Used

- Laravel
- Laravel Sanctum
- MySQL
- Postman
- REST API architecture

---

# Installation

## 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/Authentication-System-Account-Management-API.git
cd Authentication-System-Account-Management-API
```

## 2. Install dependencies

```bash
composer install
```

## 3. Create environment file

```bash
cp .env.example .env
```

## 4. Configure database

Edit `.env` file and update database credentials:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=auth_api
DB_USERNAME=root
DB_PASSWORD=
```

## 5. Generate application key

```bash
php artisan key:generate
```

## 6. Run migrations

```bash
php artisan migrate
```

This will create the required database tables including the `users` table.

## 7. Install Sanctum

```bash
composer require laravel/sanctum
```

Publish Sanctum configuration:

```bash
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```

Run migrations again:

```bash
php artisan migrate
```

## 8. Run the application

```bash
php artisan serve
```

The API will be available at:

```
http://127.0.0.1:8000
```

## API Documentation

The API can be tested using the provided Postman collection.

Steps:

1. Import the Postman collection located in `/docs`.
2. Run the Laravel server:

php artisan serve

3. Test the endpoints in the following order:

POST /api/register
POST /api/login
GET /api/me
PUT /api/me
PUT /api/me/password
POST /api/logout
DELETE /api/me

Authentication uses Laravel Sanctum tokens.

For protected routes, include the header:

Authorization: Bearer YOUR_TOKEN


## Test Scenario

1. POST /api/register → create account
2. POST /api/login → retrieve token
3. GET /api/me without token → Unauthorized
4. GET /api/me with token → success
5. PUT /api/me → update profile
6. PUT /api/me/password → change password
7. POST /api/logout → logout
8. GET /api/me with old token → Unauthorized
