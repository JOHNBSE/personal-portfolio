---
title: Property App Backend
repo_url: https://github.com/JOHNBSE/property-app-backend
excerpt: "A Laravel 12 REST API backend for a property listing / real-estate platform."
---

A Laravel-based REST API backend for a property management and real estate application, with authentication, post management, categorization, admin controls, and promotional features.

## Tech Stack

- Laravel 12, PHP 8.2+
- Laravel Sanctum (API token auth)
- SQLite by default (configurable for MySQL/PostgreSQL)
- Laravel Sail, Pail, Pint for dev tooling
- Vite for frontend asset bundling

## Features

- **Auth**: registration/login, Sanctum token auth, admin roles
- **Property posts**: create/delete listings, browse certified/trending/hot-pick/near-you/ready-for-visit posts, view tracking, "my posts"
- **Categories**: browse and filter posts by category
- **Banners & events**: public listings, admin-managed create/delete/toggle
- **Admin dashboard**: user management (grant/revoke premium), post moderation (boost/visit toggles), banner and event management

## API Overview

```
POST   /api/auth/register        - Register new user
POST   /api/auth/login           - Login user
GET    /api/posts                - List all posts
GET    /api/posts/trending       - Trending posts
GET    /api/posts/near-you       - Posts near user location
POST   /api/posts                - Create post (auth required)
GET    /api/posts/my-posts       - User's own posts (auth required)
GET    /admin/users              - List all users (admin only)
PATCH  /admin/posts/{post}/boost - Toggle boost status (admin only)
```

## Security

- Laravel Sanctum token-based API authentication
- Bcrypt password hashing
- Admin middleware for role-based access control
- CSRF and configurable CORS protection

## Running it

```bash
git clone https://github.com/JOHNBSE/property-app-backend.git
cd property-app-backend
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
npm install && npm run build
php artisan serve
```

Or via the repo's setup script: `composer run setup` then `composer run dev`.

This is a private repository — access is limited to the owner and any invited collaborators.
