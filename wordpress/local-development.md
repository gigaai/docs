# Local Development
- [Secure Tunnels to Localhost](#secure-tunnels-to-localhost)
- [Working with Frontend](#working-with-frontend)

***

<a name="secure-tunnels-to-localhost"></a>
## Secure Tunnels to Localhost

Let's assume that you want to test your bots in your development environment before deploying. You'll need to let Facebook connect to your PC and it should have SSL enabled.

To simply these step, you can use some local tunnel services to expose your localhost, for example: [ngrok](https://ngrok.com), [localtunnel](https://localtunnel.me), [serveo](https://serveo.net/), etc.

We also help the process even easier by providing the expose script if you're using NodeJS. To do so:

1. Install ngrok globally by running `npm i -g ngrok`, and config auth if you want.
1. Install NodeJS libraries by running `npm install` in `giga-messenger-bots` directory.
1. Link global ngrok to your `node_modules` by running `npm link ngrok`.
1. Edit `expose.js` with your domain. By default is `wp.dev`.
1. From Cli, run `node expose.js`

Now you get https url which can access from internet and an inspector at [http://localhost:4040](http://localhost:4040)

<a name="working-with-frontend"></a>
## Working with Frontend
We recommend you create your own CSS, JS file and hook into `admin_enqueue_scripts()` instead of editing plugin files directly. However, if you still want to edit our files, we've setup scripts to make this process easier.

Giga Messenger uses ParcelJS, and BrowserSync to compiling scripts and live reloading. First, you'll need install dependencies.

1. From `giga-messenger-bots` directory, run `npm install`, if you've followed the steps in the previous section, skip this step.
1. Run `npm run watch` to watching file changes and compiling styles and scripts for development or `npm run build` to build them on production.