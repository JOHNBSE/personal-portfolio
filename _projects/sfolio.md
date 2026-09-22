---
title: Sfolio
repo_url: https://github.com/JOHNBSE/agiegeorgia
image: /assets/images/sfolio-dashboard.svg
excerpt: "Sfolio — a multi-tenant school management platform for private primary schools: student records, fees, payroll, and academic reporting."
---

A multi-tenant school management platform for private primary schools:
student records, fees, payroll, and academic reporting, built to replace
manual, paper-based record keeping for schools that have never used
software like this before.

## Features

- **Student records** — enrollment, class assignment, guardian/contact
  details, photos, full profile pages with academic history, attendance,
  and fee standing.
- **Fees** — an Excel-style fee structure grid (per class, per term, per
  boarding type), automatic invoicing kept in sync with the live fee
  structure, payments, running balances, defaulter tracking, and PDF
  statements/receipts.
- **Payroll** — salary structures, monthly payroll runs, configurable
  statutory deductions (PAYE, NSSF), and payslip PDFs.
- **Financial reporting** — Income Statement and a simplified Balance
  Sheet (cash, receivables, fixed assets, liabilities).
- **Academic reports** — grade bands, division computation, and
  competition-ranked positions, rendered as PDF report cards matching a
  school's existing paper templates, single or in bulk.
- **Attendance** — daily student and staff registers.
- **Multi-tenancy** — row-level tenant isolation (`school_id` scoping) so
  multiple schools run on one codebase with no data leakage between them,
  plus a platform-admin tier to onboard/manage tenant schools.
- **Role-based access** — admin, teacher, bursar, and platform-admin roles
  with a permission matrix enforcing separation of duties (e.g. the person
  entering grades is never the person recording money).
- **Audit trail** — an activity log of high-value actions (marks, payments,
  payroll approvals, role changes).

## Tech stack

| Layer | Choice |
|---|---|
| Backend | Laravel 12, PHP 8.3 target (see note below) |
| Frontend | Livewire 3, Alpine.js, Tailwind CSS 3 — no SPA framework |
| Database | MySQL |
| Roles/permissions | `spatie/laravel-permission` |
| PDF generation | `barryvdh/laravel-dompdf` |
| Multi-tenancy | Row-level (`school_id` + `App\Support\Tenancy\BelongsToSchool`) |

## Requirements

- PHP 8.2+
- Composer
- Node.js + npm
- MySQL

## Setup

```bash
composer install
cp .env.example .env
php artisan key:generate
```

Configure your database in `.env`, then:

```bash
php artisan migrate --seed
npm install
npm run build
```

## Running

```bash
composer run dev
```

Runs the app server, queue listener, log tailer (`pail`), and Vite dev
server together. Or run `php artisan serve` and `npm run dev` separately.

## Testing

```bash
php artisan test
```

Every tenant-scoped feature ships with a cross-school isolation test
(seed a second school, assert zero data leakage between tenants).

Source: https://github.com/JOHNBSE/agiegeorgia
