# Setup Messenger
- [Create Facebook App & Page](#create-facebook-app-and-page)
- [Setup Webhook](#setup-webhook)
- [Setup Messenger](#setup-messenger)
- [Test Your First Message](#test-your-first-message)

***

<a name="create-facebook-app-and-page"></a>
## Create Facebook App & Page
Create a new [Facebook App](https://developers.facebook.com/quickstarts/?platform=web) and [Page](https://www.facebook.com/pages/create) or simply use existing ones. Go to the App Dashboard and under Product Settings click "Add Product" and select "Messenger."

![Setup Messenger](/images/setup-messenger.png)
<a name="setup-webhook"></a>
## Setup Webhook

In your Facebook App. Navigate to Webhooks menu item, click New Subscription, then choose Page. A dialog will shows up:
	
![New Page Subscription](/images/standalone-page-submission.gif)

- In "Callback URL", enter your webhook URL (default is `https://domain.com/giga-messenger-bot/public/`).
- In "Verify Token", enter `GigaAI`
- In "Subscription Field", check all fields with prefix "message_", like `message_deliveries`, `messages`, `messaging_optins`, `messaging_postbacks`, `message_echoes`, `message_reads`, and `messaging_account_linking`.
- Click <kbd>Verify and Save</kbd>

<a name="setup-messenger"></a>
## Setup Messenger

The next step is make a connection between Website <=> App <=> Page, so all messages come from page pass through app to website and vice versa.

- In your Facebook App. Navigate Messenger, below Webhooks item.
- In `Token Generation` section, select a your page, you'll need to confirm permission for that page. After that step, you'll got Page Access Token.
- In Webhooks box, scroll down to Select a page to subscribe your webhook to the page events. Choose your page and click "Subscribe".
![Page Access Token](/images/token-generation.gif)
- Open `giga-messenger-bot/config.php` and paste that copied text to `page_access_token` section.
- *(Optional)* Copy your page ID, paste it to `page_id` section.

Now, visit your subscribe URL (default is `https://domain.com/giga-messenger-bot/public/?subscribe=true`). You should see this message:

```
{
    success: true
}
```

> Please remember that you can visit this subscribe URL anytime to check connection status.

<a name="test-your-first-message"></a>
## Your First Message

- In your browser, open your https://domain.com/giga-messenger-bot/public/seeder.php, this file contains all nodes which you define here
- If success, you'll receive "Nodes seeded" message.

All done, now it's time to test your first message!

Try to send `hi` to your page with your app's administrator account. If you get reply from your page. Congratulation! Otherwise, please check your server requirements or previous steps.

![Greeting](/images/greeting.jpg)