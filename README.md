# Mailtrap Email Sender

A Laravel 12 app for sending emails via Mailtrap, with license-based user access and admin license management.

## Features

- User registration/login (Blade UI)
- License system: admin can create licenses, users must enter license to access email sender
- Email sending with 10+ templates
- SMTP via Mailtrap
- Role-based access (admin/user)
- Blade views for auth, license input, admin license management, and email sending

## Setup

1. Clone the repo and cd into it
2. `composer install`
3. Copy `.env.example` to `.env` and set DB/Mailtrap credentials
4. `php artisan key:generate`
5. `php artisan migrate --seed`
6. Install Laravel Breeze or Jetstream for full authentication
7. Add `CheckLicense` and `AdminMiddleware` to `app/Http/Kernel.php`:

```php
protected $routeMiddleware = [
    // ... existing
    'checklicense' => \App\Http\Middleware\CheckLicense::class,
    'admin' => \App\Http\Middleware\AdminMiddleware::class,
];
```

8. Set admin role for your admin user in DB (`role: 'admin'`)

## Usage

- Admin logs in, creates licenses
- Users register, enter license to unlock email sender
- Users send emails using templates
