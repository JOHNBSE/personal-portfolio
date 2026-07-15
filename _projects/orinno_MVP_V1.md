---
title: Orinno MVP V1
repo_url: https://github.com/JOHNBSE/orinno_MVP_V1
image: /assets/images/orinno_MVP_V1-placeholder.svg
excerpt: "Orinno is a multi-tenant property/tenancy management SaaS built on Laravel 9."
---

Orinno is a multi-tenant property/tenancy management SaaS built on Laravel 9.

## Roles

- Admin — platform owner: manages SaaS accounts, subscriptions, SMTP/system settings
- Owner — property/business owner: manages tenants, listings, invoices, staff
- Tenant — renter/client portal: tickets, invoices, documents
- Maintainer — handles maintenance requests

## Stack

- PHP 8+, Laravel 9, MySQL
- stancl/tenancy, spatie/laravel-permission, Passport/Sanctum for auth
- Payments: Stripe, PayPal, Razorpay, Mollie, Authorize.Net, Iyzico, PayTM, MercadoPago, BitPay

## Setup

```bash
composer install
npm install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed
npm run build
php artisan serve
```

Source: https://github.com/JOHNBSE/orinno_MVP_V1
