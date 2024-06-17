# ParentMD

## Local Development and Stack

The application is built on Laravel with a Vue front-end, with Statamic powering the CMS.

Local development is done inside a Docker container, conveniently managed using Laravel Sail.

To get started:

1. `cp .env.example .env`
2. Modify any ports, as necessary, inside `.env`
3. `sail up` to build your containers and run the application.
4. See if everything is working properly by visiting http://localhost:8800 (or whatever you have configured in your `.env` file)

To get started, run: `sail up` inside the project directory. If you would like to modify any ports, you can do this in your `.env` file.

### Note about Sail

When using Sail, CLI commands must be run inside the container. Sail makes this simple: https://laravel.com/docs/11.x/sail#executing-sail-commands

One thing to keep in mind is Statamic "please" commands still need "php" in the command when running, so running `php please ...` would become `sail php please ...` and not `sail please ...`. In other words, it does not act like artisan in this case.

### Useful Links

Statamic Control Panel: http://localhost:8800/cp/
