# ParentMD

## Local Development and Stack

The application is built on Laravel with a Vue front-end, with Statamic powering the CMS. Local development is done inside a Docker container, conveniently managed using Laravel Sail which stands up PostgreSQL and Mailpit locally.

### Getting Started

1. `cp .env.example .env`
2. Modify any ports, as necessary, inside `.env`
3. Install deps `docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs`
4. Add sail alias into ~/.zshrc or ~/.bashrc:
   `alias sail='[ -f sail ] && sh sail || sh vendor/bin/sail'`
5. `sail up` to build your containers and run the application.
6. Setting up an app key `sail artisan key:generate`
7. See if everything is working properly by visiting http://localhost:8800 (or whatever you have configured in your `.env` file)
8. `sail artisan migrate`
9. `sail artisan db:seed --class=DatabaseSeeder` to seed the database with a test user (test@char3.com)
10. Verify everything is working by going to http://localhost:8800/cp and using your test user to log in.
     User: test@char3.com
     Password: password

### Note about Sail

When using Sail, CLI commands must be run inside the container. Sail makes this simple: https://laravel.com/docs/11.x/sail#executing-sail-commands

One thing to keep in mind is Statamic "please" commands still need "php" in the command when running, so running `php please ...` would become `sail php please ...` and not `sail please ...`. In other words, it does not act like artisan in this case.

### Email on Local Development

Email is caught by Mailpit so you do not need to worry about local development hitting real inboxes. You can access the Mailpit Dashboard / Inbox at http://localhost:8026/ (or another port if you changed it)

### Useful Links

Statamic Control Panel: http://localhost:8800/cp/


## Comands to run

### CS (Laravel pint)

```bash
sail composer pint
```

### MD (Mass detector)

```bash
sail composer phpmd
```
