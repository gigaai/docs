# Installation
- [Site Requirements](#site-requirements)
- [Installing Giga Messenger Bots](#installing-giga-messenger-bots)
- [Secure Tunnels to Localhost](#secure-tunnels-to-localhost)

***
> 
- It's recommended that you read [Messenger Platform's Overview](https://messengerdevelopers.com/resources/platform-overview) before continuing this documentation.
- Please note that this documentation is for WordPress edition only. If you use Laravel, try [Messenger Storm](/docs/messenger-storm) documentation

<a name="site-requirements"></a>
## Site Requirements
In order to run Giga Messenger Bots, your server should meet these minimum requirements:

- PHP >= 7.1.3
- WordPress >= 4.8
- `cURL` should enabled
- Your site should be `https`. Get a free one in [LetsEncrypt](https://letsencrypt.org)

> Althought the plugin can run on PHP 5.6 but it's highly recommended that you run latest PHP 7 for better performance and security. WordPress itself recommend PHP 7.2 also.


<a name="installing-giga-messenger-bots"></a>
## Installing Giga Messenger Bots

Like other WordPress plugins, you just do some simple steps to install.

1. Download `giga-messenger-bots.zip` and unzip the package.
1. Copy `giga-messenger-bots` directory to `/wp-content/plugins` directory.
1. Activate plugin through `wp-admin/plugins` screen.
1. Done! Now navigate to Dashboard / Giga AI / Settings page and start configuring and continue reading [Setup Messenger](/docs/setup-messenger) documentation.


<a name="secure-tunnels-to-localhost"></a>
## Secure Tunnels to Localhost (For Local Development)

Let's assume that you want to test your bots in your development environment before deploying. You'll need to let Facebook connect to your PC and it should have SSL enabled.

To simply these step, you can use some local tunnel services to expose your localhost, for example: [ngrok](https://ngrok.com), [localtunnel](https://localtunnel.me), [serveo](https://serveo.net/), etc.

We also help the process even easier by providing the expose script if you're using NodeJS. To do so:

1. Install NodeJS libraries by running `npm install` in `giga-messenger-bots` directory.
1. Edit `expose.js` with your domain. By default is `wp.dev`.
1. From Cli, run `node expose.js`

Now you get https url which can access from internet and an inspector at [http://localhost:4040](http://localhost:4040)