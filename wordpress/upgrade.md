# Upgrade Guide
---
## Upgrading to 2.0 from 1.x

> We do not directly support upgrade to 2.0 from 1.x. You have to backup your database, copy your nodes to another locations and manual enter again. 

- Backup your whole database. Uninstall and then Delete your old `giga-messenger-bot` directory
- Do a fresh install like [Installation Guide](/docs/wordpress/installation).
- If you're hooking to `fmb_pre_run` action. Change to `giga_pre_seed`.
- Text Matching has slightly changed. If you just use `%` syntax. Forget it. Otherwise, read [Text Matching](/docs/wordpress/text-matching) guide again.