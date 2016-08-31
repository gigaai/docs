# Storage Drivers
---
By default, for simply your application, Giga AI stores your leads in `cache/data.json` file, this is good for small or testing environment application. For large application, we'd recommended you use `mysql` or `wordpress` storage driver.

## Different between `mysql` and `wordpress`

Both `mysql` and `wordpress` are support MySQL. But `mysql` uses [illuminate/database](https://github.com/illuminate/database) package to works with MySQL, whilst `wordpress` use native WordPress `$wpdb` object. So there are some pros and cons:

**mysql**: requires PHP 5.4+ and running `composer update` but more powerful, works with any application. Don't worry, composer is easy to use.

**wordpress**: You can run it without configuration, but only works with WordPress.

You can use `mysql` storage driver for all app including WordPress but cannot use `wordpress` for any app.

## Installing MySQL Storage Driver

Because MySQLStorageDriver uses `illuminate/database` and it requires PHP 5.4+, before you installing `mysql` driver. Please make sure your server is running PHP 5.4+

1. Go to your project root in the same directory with `composer.json`, and add this package:
```
"illuminate/database": "5.0.*"
```
So your `composer.json` should become like so:
```
    {
        "require": {
            "gigaai/framework": "dev-master",
            "illuminate/database": "5.0.*"
        }
    }
```
1. Then update packages
```
composer update
```
1. Open `config.php`
    - Change `storage_driver` to `mysql`
    - In `mysql` section, enter your database connection info.
1. Import `vendor/gigaai/schema/mysql.sql` to your database, this will setup db tables for you. If you want to set table prefix, please edit that file manually before importing.
