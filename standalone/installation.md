# Installation
- [Installation](#installation)
	- [Server Requirements](#server-requirements)
	- [Installing Giga Messenger Bot](#installing-giga-messenger-bot)
	- [Secure Tunnels to Localhost](#secure-tunnels-to-localhost)

***
> 
- This installation guide is applied for PHP Standalone version. If you're using WordPress plugin. Go to [WordPress](/docs/wordpress) documentation instead.
- It's recommended that you read [Messenger Platform's Overview](https://developers.facebook.com/docs/messenger-platform/product-overview) before continuing this documentation.


<a name="installation"></a>
## Installation

<a name="server-requirements"></a>
### Server Requirements
In order to run Giga Messenger Bots (GigaAI), your server should meet these minimum requirements:
- PHP >= 5.4
- MySQL >= 5.6
- `cURL` should enabled
- Your site (or webhook) should `https`

Most of server/hosting providers is already support PHP 5.4+ and cURL. You can also get a free SSL from [LetsEncrypt](https://letsencrypt.org). 

Of course, it's highly recommended that you run latest stable PHP version.

<a name="installing-giga-messenger-bot"></a>
### Installing Giga Messenger Bot
- Download `giga-messenger-bot.zip` and unzip the package.
- Copy `giga-messenger-bot` directory to your web server.
- Your webhook now is the path to `/public/index.php` URL. For example: `https://domain.com/giga-messenger-bot/public/index.php`.

#### Setup Your Database
- Create your MySQL database (or use existing one if already have)
- Open `/vendor/gigaai/framework/schema/mysql.sql` and import to your database
- Open `/config.php`, in mysql section, enter your database connection info then save file.

> Of course, you can rename `giga-messenger-bot` to whatever you want. Or point your domain to `/public/` URL for security purpose. All is well.

<a name="secure-tunnels-to-localhost"></a>
### Secure Tunnels to Localhost
Let's assume that you want to test your bots in your development environment before deploying. You'll need to let Facebook connect to your PC and it should have SSL enabled. To simply these steps, we'd recommend that you use [ngrok](https://ngrok.com), it will automatically create a secure public URL to your local webserver with format: `https://RANDOM.ngrok.io`.