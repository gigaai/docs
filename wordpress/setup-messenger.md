# Setup Messenger
***

## Create Facebook App & Page
Create a new [Facebook App](https://developers.facebook.com/quickstarts/?platform=web) and [Page](https://www.facebook.com/pages/create) or simply use existing ones. Your Facebook App can remain in sandbox mode and your Page does NOT have to be publicly visibile. The Page profile picture and name will be used to form the "identity" of your bot and is what people will see when they engage it.

## Setup Webhook

- In your Facebook App. Navigate to Webhooks menu item, click New Subscription, then choose Page. A dialog will shows up:
	
	![New Page Subscription](https://gigaai.com/images/new-page-subscription.jpg)
    
    - In "Callback URL", enter your webhook URL (default is `https://yourwebsite.com/messenger`).
    - In "Verify Token", enter `GigaAI`
    - In "Subscription Field", check `message_deliveries`, `messages`, `messaging_optins`, and `messaging_postbacks`
    - Click <kbd>Verify and Save</kbd>

If these above steps succeed, you'll see this:
![Webhook Success](https://gigaai.com/images/webhook.jpg)

## Setup Messenger
The next step is make a connection between Website <=> App <=> Page, so all messages come from page pass through app to website and vice versa.

- In your Facebook App. Navigate Messenger, below Webhooks item.
- In `Token Generation` section, select a your page, you'll need to confirm permission for that page. After that step, you'll got Page Access Token.
![Page Access Token](https://gigaai.com/images/token-generation.jpg)
- Click to copy that token, go to Facebook Messenger Bots settings and paste that in Page Access Token input
- *(Optional)* Go to your FB page, jump to About tab, copy Facebook Page ID to Page ID input in Facebook Messenger Bots settings
	![Page ID](https://gigaai.com/images/facebook-page-id.jpg)
- Click <kbd>Save Changes</kbd>

- Now, visit your subscribe URL (default is `https://yourwebsite.com/messenger/subscribe`). If you see a message:

<div class="h1">Congratulation! Facebook Bot is successfully subscribed your webhook.</div>

Congratulation. Your bot is ready!

> Please remember that you can visit this subscribe URL anytime to check connection status.
