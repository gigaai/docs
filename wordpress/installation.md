# Installation

> It's recommended that you read [Messenger Platform's Overview](https://developers.facebook.com/docs/messenger-platform/product-overview) before continue reading this documentation.

***

## Installation

### Site Requirements
Giga Messenger Bot (GigaAI) has been tested and compatibility with

- WordPress 4.0+
- PHP 5.3+
- `cURL` should enabled
- Your site (or webhook) should `https`

However, it's highly recommended that you run latest WordPress & PHP version.

### Installing Giga
1. Download `giga-ai.zip` and unzip the package
1. Upload `giga-ai` folder to the `wp-content/plugins/` directory
1. Activate the plugin through the Plugins menu in WordPress
1. Start using the plugin through the menu `Settings\Giga AI`

### Configure Webhook
After activated, if your website has **permalink** enabled, FMB will automatically creates two links which are: `https://yourwebsite.com/messenger/` (webhook) and `https://yourwebsite.com/messenger/subscribe` (subscribe). Try accessing these URLs to verify if it works (They shouldn't show 404 or some of your pages with content).

If your website doesn't have **permalink** enabled, or `/messenger/` and `/messenger/subscribe` doesn't work. Don't worry! You can create them manually by go to `Dashboard\Pages\Add New` and then create page with template `Messenger Subscribe` and `Messenger Webhook`. You're free to name their URLs.

### Secure Tunnels to Localhost
Let's assume that you want to test your bots in your development machine before deploy. You'll need to let Facebook connect to your pc and it should have SSL enabled. We'd recommend that you use [ngrok](https://ngrok.com), it will automatically creates a secure public URL to your local webserver with format: `https://random_md5.ngrok.io`.