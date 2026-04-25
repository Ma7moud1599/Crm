# Laravel CRM

A production-ready Customer Relationship Management API built with Laravel. Features event sourcing, multi-tenancy, and a clean RESTful API following JSON:API spec conventions.

## Features

- **Contacts Management** — full CRUD with filtering and sorting via `spatie/laravel-query-builder`
- **Interactions Tracking** — log calls, emails, meetings and other touchpoints per contact
- **Event Sourcing** — every state change is recorded as an immutable event using `spatie/laravel-event-sourcing`
- **Multi-tenancy** — isolated tenant databases powered by `stancl/tenancy`
- **JSON:API Responses** — consistent, spec-compliant API responses via `timacdonald/json-api`
- **Enum-driven Status** — typed enums for interaction types and contact statuses using `spatie/laravel-enum`

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Laravel |
| Auth | Laravel Sanctum |
| API Response | timacdonald/json-api |
| Query Filtering | spatie/laravel-query-builder |
| Event Sourcing | spatie/laravel-event-sourcing |
| Multi-tenancy | stancl/tenancy |
| Enums | spatie/laravel-enum |
| HTTP Status Codes | juststeveking/http-status-code |
| Database | MySQL |

## Architecture

```
app/
├── Http/
│   └── Controllers/
│       └── Api/
│           ├── Contacts/
│           │   ├── IndexController.php
│           │   ├── ShowController.php
│           │   ├── StoreController.php
│           │   ├── UpdateController.php
│           │   └── DeleteController.php
│           └── Interactions/
│               ├── IndexController.php
│               ├── ShowController.php
│               ├── StoreController.php
│               ├── UpdateController.php
│               └── DeleteController.php
```

Single-action controllers keep each HTTP operation focused and independently testable.

## API Endpoints

### Contacts

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/contacts` | List contacts (filterable, sortable) |
| GET | `/api/contacts/{id}` | Get a contact |
| POST | `/api/contacts` | Create a contact |
| PATCH | `/api/contacts/{id}` | Update a contact |
| DELETE | `/api/contacts/{id}` | Delete a contact |

### Interactions

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/interactions` | List interactions |
| GET | `/api/interactions/{id}` | Get an interaction |
| POST | `/api/interactions` | Log a new interaction |
| PATCH | `/api/interactions/{id}` | Update an interaction |
| DELETE | `/api/interactions/{id}` | Delete an interaction |

## Installation

```bash
git clone https://github.com/Ma7moud1599/Crm.git
cd Crm

composer install
cp .env.example .env
php artisan key:generate

# Configure DB credentials in .env, then:
php artisan migrate
php artisan serve
```

A `Makefile` is included with common shortcuts:

```bash
make migrate   # run migrations
make test      # run test suite
```

## License

MIT
