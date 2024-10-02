# Metricalo Payment Gateway

Metricalo Payment Gateway is a Laravel-based payment processing system that interacts with two external payment systems: Shift4 and ACI. It provides an API endpoint and CLI command for handling transactions and returning a unified response from either payment system.

## Features

- Process payments using Shift4 or ACI systems
- Unified response format for consistency
- API endpoint to trigger payments via HTTP
- CLI command to process payments via terminal
- User registration and login system
- Payment confirmation and failed transaction pages
- Simple, responsive UI for payment forms

## Requirements

- PHP 8.0 or higher
- Composer
- Laravel 9.x
- MySQL (or compatible database)
- Git
- Docker (optional for containerization)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Peter2020-tech/metricalo_payment_gateway.git

    Navigate to the project directory:

    bash

cd metricalo_payment_gateway

Install the dependencies:

bash

composer install

Copy the .env file and configure your environment settings:

bash

cp .env.example .env

Generate an application key:

bash

php artisan key:generate

Configure the database in your .env file:

bash

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=paynow
DB_USERNAME=root
DB_PASSWORD=

Run the migrations:

bash

    php artisan migrate

    (Optional) Set up Docker:
        Create a Dockerfile (if you haven’t done so) and use Docker to containerize your app.

Usage
API Endpoint

The API endpoint allows users to process a payment via HTTP.

Endpoint:

bash

POST /app/example/{aci|shift4}

Parameters:

    amount: Transaction amount
    currency: Currency code (e.g., USD, EUR)
    card_number: Card number
    card_exp_year: Expiration year
    card_exp_month: Expiration month
    card_cvv: Card CVV code

Example:

bash

curl -X POST http://localhost:8000/app/example/shift4 \
  -H "Content-Type: application/json" \
  -d '{"amount": 100, "currency": "USD", "card_number": "4242424242424242", "card_exp_year": "2024", "card_exp_month": "12", "card_cvv": "123"}'

CLI Command

The CLI command allows users to process a payment via the terminal.

Command:

bash

php artisan app:example {aci|shift4}

Example:

bash

php artisan app:example shift4

User Interface

The system provides a simple web interface where users can register, log in, and make payments. To view it:

    Start the Laravel development server:

    bash

    php artisan serve

    Visit http://localhost:8000 to access the web interface.

Authentication

    Users can register and log in to view the secured pages, such as payment_detail, payment_confirmation, and failed_transaction.
    Secured routes are protected via middleware and require authentication.

Testing

You can run the following tests (unit, integration, functional) using Laravel's built-in test suite:

bash

php artisan test

Docker (Optional)

To run the project using Docker, follow these steps:

    Build the Docker image:

    bash

docker build -t metricalo_payment_gateway .

Run the container:

bash

docker run -p 8000:8000 metricalo_payment_gateway
