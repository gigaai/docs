# Installation
- [Installation](#installation)
	- [Site Requirements](#site-requirements)
	- [Secure Tunnels to Localhost](#secure-tunnels-to-localhost)
	- [Installing Giga Messenger Bot](#installing-giga-messenger-bot)

***
> 
- It's recommended that you read [Messenger Platform's Overview](https://developers.facebook.com/docs/messenger-platform/product-overview) before continuing this documentation.
- Please note that this documentation is for WordPress version only. If you use PHP package, try [PHP Standalone](/docs/standalone) documentation

<a name="installation"></a>
## Installation

<a name="site-requirements"></a>
### Site Requirements
In order to run Giga Messenger Bot (GigaAI), your server should meet these minimum requirements:

- PHP >= 5.4
- WordPress >= 4.4
- `cURL` should enabled
- Your site (or webhook) should `https`

Almost server/hosting providers already support PHP 5.4+ and cURL. You can also get a free SSL from [LetsEncrypt](https://letsencrypt.org/). However, it's highly recommended that you run latest stable WordPress & PHP version.

<a name="secure-tunnels-to-localhost"></a>
### Secure Tunnels to Localhost

Let's assume that you want to test your bots in your development environment before deploying. You'll need to let Facebook connect to your PC and it should have SSL enabled. To simply these steps, we'd recommend that you use [ngrok](https://ngrok.com), it will automatically create a secure public URL to your local webserver with format: `https://RANDOM.ngrok.io`.


<a name="installing-giga-messenger-bot"></a>
### Installing Giga Messenger Bots

Like other WordPress plugins, you just do some simple steps to install.

1. Download `giga-messenger-bots.zip` and unzip the package.
1. Copy `giga-messenger-bots` directory to `/wp-content/plugins` directory.
1. Activate plugin through `wp-admin/plugins` screen.
1. Done! Now navigate to Dashboard / Giga AI / Settings page and start configuring. You can see the webhook is *https://domain.com/wp-json/giga-ai/webhook* under the Basics section.

