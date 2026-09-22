---
title: Orinno
repo_url: https://github.com/orinno-co-limited/app_orinno
image: /assets/images/orinno-admin-dashboard.svg
excerpt: "Orinno — a property/rental management platform (Laravel 9) with separate admin, owner, tenant, and maintainer portals."
---

Orinno is a property/rental management platform built on Laravel 9. It handles
listings, tenants, owners, maintenance requests, invoicing (including
recurring invoices), and payments, with separate portals per role.

**Owner dashboard:**

![Owner dashboard](/assets/images/orinno-owner-dashboard.svg)

**Tenant dashboard:**

![Tenant dashboard](/assets/images/orinno-tenant-dashboard.svg)

## Roles

- **Admin** — platform configuration, users, SMS/reminder settings.
- **Owner** — manages properties, listings, tenants, invoices.
- **Tenant** — views agreements, invoices, and maintenance requests.
- **Maintainer** — handles maintenance issues assigned to them.

## Features

- Property listings and agreements
- Recurring invoice generation with automated rent reminders (WhatsApp/SMS)
- Multiple payment gateways (Stripe, Razorpay, PayPal, Mollie, Iyzico, MercadoPago, and more)
- KYC verification
- Notification system (mail, SMS, WhatsApp Cloud API)

## Requirements

- PHP ^8.0.2 with the `zip` extension
- Composer
- MySQL
- Node.js (for asset building via Vite)

## Setup

```bash
composer install
cp .env.example .env
php artisan key:generate
# configure DB_* and other credentials in .env
php artisan migrate
npm install
npm run dev   # or: npm run build
php artisan serve
```

## Testing

```bash
php artisan test
```

Source: https://github.com/orinno-co-limited/app_orinno
