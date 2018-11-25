# Troubleshooting
---
These are some common issues you may run into while setting up Giga Messenger. If you encounter something that is not listed here, feel free to raise a question on the [support forum](https://giga.ai/support) or create an issue on [Github](https://github.com/gigaai/framework).

### Bot doesn't responses any one except me?
Your app needs `pages_messaging` permission to public. Please see and follow [Official Facebook guide](https://developers.facebook.com/docs/messenger-platform/app-review).

There're some [policies](https://developers.facebook.com/docs/messenger-platform/policy-overview) which of Facebook to protect spamming content also, please read carefully.

### I already have `pages_messaging` permission bot my bot still doesn't responses any one except me?
Your app status is private, please public it.

### My webhook URL doesn't works, it returns 404, redirects to another pages?
We use native WP-API to handle requests between our plugin and Facebook. Please make sure:
- Your permalink setting works.
- Your `mod_rewrite` is enabled.