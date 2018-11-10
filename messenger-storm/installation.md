# Installation
- [Installation](#installation)
	- [Site Requirements](#site-requirements)
	- [Secure Tunnels to Localhost](#secure-tunnels-to-localhost)
	- [Installing Messenger Storm](#installing-messenger-storm)

***
> 
- It's recommended that you read [Messenger Platform's Overview](https://messenger.fb.com) before continuing this documentation.
- Please note that this documentation is for Laravel version only. If you use WordPress, try [WordPress](/docs/) documentation

<a name="installation"></a>
## Installation

<a name="site-requirements"></a>
### Site Requirements
Messenger Storm built on top of Laravel and Giga AI framework so the server requirements is exactly same as Laravel.

- PHP >= 7.1.3
- OpenSSL PHP Extension
- PDO PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
- Curl PHP Extension
- A Https Address

<a name="secure-tunnels-to-localhost"></a>
### Secure Tunnels to Localhost

Let's assume that you want to test your bots in your development environment before deploying. You'll need to let Facebook connect to your PC and it should have SSL enabled. To simply these steps, we'd recommend that you use [ngrok](https://ngrok.com), it will automatically create a secure public URL to your local webserver with format: `https://RANDOM.ngrok.io`.

If you're using [Valet](https://laravel.com/docs/5.4/valet), you can simply use `valet secure site-name.dev` syntax

<a name="installing-messenger-storm"></a>
### Installing Messenger Storm
Install Messenger Storm is same as normal Laravel application, however, we do ship with optimized `vendor` directory already so you don't have to run `composer update`.

1. Download `messenger-storm.zip` from our [Dashboard](/dashboard)
1. Copy and unzip to your server (you should create a virtual host and point)
1. Open `.env` and edit with your server information.
1. From bash, run `php artisan migrate` to create database tables.
1. After data is migrated, run `php artisan db:seed` to seed default data.

#### Directory Permissions
After installing Messenger Storm, you may need to configure some permissions. The  `storage` and the `bootstrap/cache` directories should be writable by your web server or Messenger Storm won't run.

Now open your website address, if you see this screen, that's perfect!
![Messenger Storm Home](/images/messenger-storm-home.png)

To access dashboard, go to:
```
URL: https://yourdomain.com/dashboard
User: admin@messenger
Password: messengerstorm
```
You should change your email and password after access!

![Messenger Storm Dashboard](/images/messenger-storm-dashboard.png)

<a name="installation-service"></a>
### Installation Service
If you do a business and don't want to take so much time for installing and setting up web server, database, we do have [Installation Service](/services/installation) for you with $49. We use [Laravel Forge](https://forge.laravel.com) which ships with latest stacks for you: Ubuntu 16.04, PHP 7.1, MariaDB, Nginx, Laravel, Giga AI latest stable version.