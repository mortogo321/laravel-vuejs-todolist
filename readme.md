# Todo List (Laravel + Vue)

A task-management demo app: create categories, assign tasks ("jobs") to users, and manage everything through a role-gated admin panel.

## What's inside

- Email/password authentication — register, login, password reset (Laravel's built-in auth scaffolding)
- Personal task list — each user sees the jobs assigned to them and can edit their own
- Task categories for organizing jobs
- Admin panel, gated by a custom `role:admin` middleware, for managing categories, jobs, and users
- File attachment download endpoint for tasks
- A separate `roles` table (`admin`, `editor`, default `user`) decoupled from the users table

## Tech stack

- Laravel (PHP), Laravel Tinker
- Vue, Vite, Bootstrap, dayjs, axios
- MySQL (default database connection)

## Quickstart

```bash
composer install
cp .env.example .env
php artisan key:generate
```

Set your database credentials in `.env` (defaults to MySQL, database `todo_list`), then:

```bash
php artisan migrate
php artisan db:seed        # optional: seeds demo users, roles, and categories

npm install
npm run dev                # or `npm run build` for production assets

php artisan serve
```

Demo login after seeding: `admin@todolist.com` / `Password@01` (admin role).

## Key routes

- `/home` — job list for the logged-in user
- `/edit/{id}` — edit a job assigned to you
- `/attache/{type}/{id}/{name}` — download a job's attached file
- `/admin/category`, `/admin/job`, `/admin/user` — admin CRUD, requires the `admin` role
