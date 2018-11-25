# Upgrade Guide
---
## Upgrading to 3.x
Since Facebook upgraded their API, Policy, and breaking changes so frequently so making LTS version stategy doesn't works with Facebook. You can't upgrade to 3.x from 2.x. You should upgrade to our latest version to use latest Facebook API.

PHP 5.6 and even 7.0 EOL is 2018 so we don't support these version. [WordPress recommend PHP 7.2](https://wordpress.org/about/requirements/) also. Although our plugin can work on 5.6, you should use at your own risk.

MySQL 5.7+ with `utf8mb4` charset is required for emoji, better meta data searching since we use json field for better performance instead of custom `_meta` table.

To upgrade, make sure your server meets our requirements, backup old plugin, replace whole old `giga-messenger-bots` directory with our new version.

## Upgrading to latest version from 2.0.x
- Make sure you've backed up your database before update any plugin.
- Replace whole old `giga-messenger-bots` folder with new downloaded folder.
- That's all.