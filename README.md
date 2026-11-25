# StaffOps

StaffOps is a software engineering course project for managing employee leave, work arrangements, and attendance. Employees submit and track requests, managers review requests from their teams, and HR manages employee accounts and attendance.

## Planned features

- Manage companies, departments, employee accounts, roles, and reporting relationships.
- Submit and approve leave and work arrangement requests.
- Import check-in and check-out events from a card-reader API and calculate worked hours.

## Technology

StaffOps is designed around a React frontend with Redux, a Laravel REST API, and a MariaDB database.

## Local development

The `backend/` directory contains Laravel 13. The `frontend/` directory contains React with Vite. The initial Laravel scaffold uses SQLite locally.

Use PHP 8.5 with the [Laravel PHP extensions](https://laravel.com/docs/13.x/deployment#server-requirements) and PDO SQLite, a [current Composer 2 release](https://getcomposer.org/download/), and Node.js 22.12 or newer.

On Ubuntu with PHP 8.5 already installed from the PHP PPA, install the missing extensions with `sudo apt update` followed by `sudo apt install php8.5-xml php8.5-mbstring php8.5-sqlite3 php8.5-curl`.

From the repository root, set up the backend in one terminal and leave its server running:

```bash
cd backend
php8.5 "$(command -v composer)" install
cp -n .env.example .env
php8.5 artisan key:generate
touch database/database.sqlite
php8.5 artisan migrate
php8.5 artisan serve
```

If `php` already points to PHP 8.5, you can use `php` in these commands. Open [the Laravel health check](http://localhost:8000/up).

In another terminal, start Vite from the repository root:

```bash
npm --prefix frontend ci
npm --prefix frontend run dev
```

Open the URL Vite prints, usually [http://localhost:5173](http://localhost:5173).

## Documentation

- [Requirements](docs/requirements.md)
- [System architecture and C4 container diagram](docs/architecture.md)
- [UML use-case diagram](docs/diagrams/use-cases.png)
- [Database design](docs/database.md)
