# Account Linking
---
Sometimes, you'll need to check that current lead is exists in your website to send useful information to them. Account Linking was born to help you do that.

## Setup Account Linking
The Account Linking feature is available in Premium edition and enabled by default. You don't have to do anything!

## Change Account Linking URL
By default, account linking URL is your login form located at `/wp-login.php`, if you want to change account linking URL. Go to `Dashboard \ Giga AI \ Settings \ Account Linking` and change the URL.

## Sending Login Button
To send Login Button, you can create any button of type `account_link`. The button can be in buttons group, carousel, or list.

## Sending Logout Button
To send Logout Button, you can create any button of type `account_unlink`. The button can be in buttons group, carousel, or list.

## Check if Lead is Logged in
By default, the `linked_account` field of lead is set to `NULL`, after logged in, it set to the current user id in `wp_users` table. You can use Storage API to check:

```
$bot->storage->get($lead_id, 'linked_account');
```