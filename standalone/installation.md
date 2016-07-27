# Installation

> 
- This installation guide is applied for PHP Standalone version. If you're using WordPress plugin. Go to [WordPress](/docs/wordpress) documentation instead.
- It's recommended that you read [Messenger Platform's Overview](https://developers.facebook.com/docs/messenger-platform/product-overview) before continue reading this documentation.

***

## Installation

### Server Requirements
In order to run Giga Messenger Bot (GigaAI), your server should meet these minimum requirements:

- PHP 5.3+
- `cURL` should enabled
- Your site (or webhook) should `https`

Most of server/hosting providers is already support PHP 5.3+ and cURL. You can also get a free SSL from [LetsEncrypt](https://letsencrypt.org). 

Of course, it's highly recommended that you run latest stable PHP version.

### Installing Giga Messenger Bot
- Download `giga-messenger-bot.zip` and unzip the package.
- Copy `giga-messenger-bot` directory to your web server.
- Set CHMOD read-writable permission to your `/giga-messenger-bot/cache/` directory.
- Your webhook now is the path to `/public/` URL. For example: `https://domain.com/giga-messenger-bot/public/`.

> Of course, you can rename `giga-messenger-bot` to whatever you want. Or point your domain to `/public/` URL for security purpose. All is well.

### Secure Tunnels to Localhost
Let's assume that you want to test your bots in your development machine before deploying. You'll need to let Facebook connect to your PC and it should have SSL enabled. To simply these steps, we'd recommend that you use [ngrok](https://ngrok.com), it will automatically creates a secure public URL to your local webserver with format: `https://RANDOM.ngrok.io`.