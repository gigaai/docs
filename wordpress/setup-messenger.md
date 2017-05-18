# Setup Messenger
- [Create Facebook App & Page](#create-facebook-app-and-page)
- [Add App Products](#add-app-product)
- [Setup Webhook](#setup-webhook)
- [Setup Messenger](#setup-messenger)
- [Update Plugin Settings](#update-plugin-settings)
- [Test Your First Message](#test-your-first-message)

***

<a name="create-facebook-app-and-page"></a>
## Create Facebook App & Page

If you've already have Facebook App & Page, skip this step. Otherwise, create a new [Facebook App](https://developers.facebook.com/quickstarts/?platform=web) and [Page](https://www.facebook.com/pages/create). Perhaps [create Facebook App guide](/tips/how-to-create-facebook-app) will helps.

<a name="add-app-product"></a>
## Add App Products
Now we'll need to add **Webhooks** and **Messenger** products to your app. 
- Click <kbd>+ Add Product</kbd> in the menu
- Onn **Webhooks** and **Messenger**, click <kbd>Get Started</kbd>.
![Add FB Apps Products](/images/add-product.gif)
 
<a name="setup-webhook"></a>
## Setup Webhook

Now navigate to Webhooks menu item, select **Page** and click <kbd>Subscribe to this topic</kbd> you'll see a dialog.
![Facebook Webhook Subscribe](/images/webhook-subscribe.gif)

- In "Callback URL", enter your webhook URL which you can find in Settings page (default is `https://domain.com/wp-json/giga-ai/webhook`).
- In "Verify Token", enter `GigaAI`
- Click <kbd>Verify and Save</kbd>

<a name="setup-messenger"></a>
## Setup Messenger
Now we have a webhook which ping Page events to our server. We'll need to tell which Facebook Pages and Events to ping.

- Click on the Messenger menu item.
- In `Token Generation` section, select a your page, you'll need to confirm permission for that page. After that step, you'll got Page Access Token.
- In Webhooks box, click <kbd>Edit events</kbd> or <kbd>Setup Webhooks</kbd> if you didn't do the previous step, you'll see this dialog:
![Edit Page Subscription Fields](/images/edit-page-subscription-fields.png)
- Select all items (we'll talk about this later), and click <kbd>Save</kbd>
- In **Select a page to subscribe your webhook to the page events** section, select your page and click <kbd>Subscribe</kbd>

<a name="update-plugin-settings"></a>
## Update Plugin Settings
Now your server can retrieve message from Facebook, we need to update Access Token in Settings page so your server can send message back.

In WP Admin, navigate to **Giga AI \ Settings \ Basics**
![Giga Messenger Settings](/images/giga-messenger-settings.png)
1. In **Page ID** box, enter your [Facebook Page ID](/tips/how-to-get-facebook-page-id).
1. In **Page Access Token**, paste the Page Access Token you've received from the previous step.
1. In **Page Name**, enter page name for manage.
1. That's all.

<a name="test-your-first-message"></a>
## Your First Message

If you reached this step. Congratulation! All easy right? Now it's time to talk with your bot

Try to send hi to your page with your app's administrator account. If you get reply from your page. Congratulation! Otherwise, please check your server requirements and previous steps.

![Greeting](/images/greeting.jpg)