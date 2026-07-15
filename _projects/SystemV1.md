---
title: RentDesk / SystemV1
repo_url: https://github.com/JOHNBSE/SystemV1
image: /assets/images/SystemV1-placeholder.svg
excerpt: "RentDesk — a multi-tenant property management system (practice project)."
---

RentDesk is a Laravel REST API for property management with Admin, Owner, and Tenant roles. It includes a vanilla JS UI served by Laravel and an optional React frontend in `frontend/` for comparison.

## Notes

This project was created as an AI-assisted practice project: treat it as a training ground and audit for security issues before trusting with real data.

## Running it

```bash
composer install
cp .env.example .env
php artisan migrate --seed
php artisan serve --port=8000
```

Seeded accounts (password: `password`): admin@example.com, owner@example.com, tenant@example.com

Source: https://github.com/JOHNBSE/SystemV1
