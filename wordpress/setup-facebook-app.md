# Setup Facebook App
- [Create Facebook App & Page](#create-facebook-app-and-page)
- [Connect Your Website to Facebook App](#connect-your-website-to-facebook-app)
- [Adding App Products](#adding-app-product)
    - [Configure Facebook Login Product](#configure-facebook-login)
    - [Configure Webhooks Product](#configure-webhooks)
    - [Configure Messenger Product](#configure-messenger)
- [Create New Bot](#create-new-bot)
- [Test Your First Message](#test-your-first-message)

***

> Although you can use only Page ID and Page Access Token to create bots, we recommend you manage pages via Facebook App so you can use many cool advanced features like faster bots creation, ID Matching, NLP, etc.

<a name="create-facebook-app-and-page"></a>
## Create Facebook App & Page

If you've already have Facebook App & Page, skip this step. Otherwise, create a new [Facebook App](https://developers.facebook.com/quickstarts/?platform=web) and [Page](https://www.facebook.com/pages/create). Perhaps [create Facebook App guide](/tips/how-to-create-facebook-app) will helps.

![Create New App](/images/docs-create-new-app.png)

<a name="connect-your-website-to-facebook-app"></a>
## Connect Your Website to Facebook App
1. Open Facebook app settings pages, navigate to **Settings / Basics** section.
1. In **App Domains** text box, enter your domain, for example: giga.ai
1. Navigate to the last section of Settings page, click <kbd>+ Add Platform</kbd> button.
1. Click **Website**
1. New **Website** section will show up, enter your website URL. For example: https://giga.ai
1. *(Optional)* Enter other fields, some will be required when you submit your app for Facebook staff to review.
1. Click **Save Changes**
1. Copy App ID and App Secret to paste to **Giga AI / Settings** page.

Now Facebook can accept connection from your website to your app. Next step is let your website connect to Facebook.

1. From your WordPress Dashboard open **Giga AI / Settings** page.
1. Copy Facebook App ID and App Secret which mentioned on the step above, leave the **Requires Permissions** field blank.
1. Hit **Save Changes**

![App Settings](/images/docs-app-settings-basic.png)


<a name="adding-app-product"></a>
## Adding App Products
From now on, your website can connect and retrieves request from Facebook. You can add as many as products you want. In this case, we'll add three essential products: **Facebook Login**, **Webhooks**, and **Messenger**.

- **Facebook Login**, as its name, lets you add Login with Facebook button to your website so people have easy way to connect to your website.
- **Webhook** lets your website retrieve update from Facebook server.
- **Messenger** helps you customize Messenger, and, of course, create Messenger bot.

To add FB app products:
1. Go to Facebook app, on the **PRODUCTS** section of the sidebar, click (+) to start adding products.
1. Under **Facebook Login**, **Webhooks**, and **Messenger**, click <kbd>Set Up</kbd>

<a name="configure-facebook-login"></a>
### Configure Facebook Login Product
Facebook Login is Giga AI built in feature, when you add Facebook Login product, ignore the **Quick Start** form and nagivate to **Facebook Login / Settings** page.

1. In **Valid OAuth Redirect URIs** text box, enter: `https://your-website.com/wp-login.php?action=fb-login`
1. Leaves other fields blank and **Save Changes**.

<a name="configure-webhooks"></a>
### Configure Webhooks Product
1. Go to **Webhooks** page under PRODUCTS section.
1. From the dropdown, select **Page** and click **Subscribe to this object**, a dialog will show up.
1. In "Callback URL", enter your webhook URL which you can find in Settings page (default is `https://domain.com/wp-json/giga-ai/webhook`).
1. In "Verify Token", enter `GigaAI`
1. Click <kbd>Verify and Save</kbd>

![Facebook Webhook Subscribe](/images/webhook-subscribe.gif)

<a name="configure-messenger"></a>
### Configure Messenger Product
1. Go to Messenger page under PRODUCTS section.
1. In Webhooks section of Messenger settings page, click <kbd>Edit events</kbd>.
1. Check all events and click **Save**

<a name="connect-your-accounts"></a>
## Connect Your Accounts
Now you can create bots with Page ID and Page Access Token, let's make it easier by connect WordPress your account to Facebook so you can select a page to add bot instead of manually enter these information.

1. In WordPress Dashboard, go to **Users / Your Profile** page.
2. Under Facebook Connect section, click **Connect**.
3. There will be a FB dialog will display ask for permissions. Accept and you're now connected with Facebook.

![Facebook Connect](/images/docs-facebook-connect.png)

<a name="create-new-bot"></a>
## Create New Bot
You've reached last step so far. Now it's easiest step, create new bot.
1. In WP Dashboard, go to **Giga AI** page.
1. Click Add New Bot, a dialog will show up.
1. Select a page which you want to add your bot, and click **Save Changes**
1. Done, you'll be redirected to Settings page.

![Create New Bot](/images/docs-create-new-bot.png)

<a name="test-your-first-message"></a>
## Your First Message

Congratulation! You've successfully built your bot. All easy right? Now it's time to talk with your bot

Try to send hi to your page with your app's administrator account. If you get reply from your page. Congratulation! Otherwise, please check your server requirements and previous steps.

![Greeting](/images/greeting.jpg)

## Now What?
- Continue with each guide in the the documentation menu.
- If you can't get this to work, see [Troubleshooting](/docs/troubleshooting) page. Remember that you're always welcome to ask a question in the [support forum](/support).

![Congratulation](/images/congratulations.png)