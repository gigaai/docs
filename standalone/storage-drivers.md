# Storage Drivers
---
By default, for simply your application, Giga AI stores your leads in `cache/data.json` file, this is good for small or testing environment application. For large application, we'd recommended you use `mysql` or `wordpress` storage driver.

## Different between `mysql` and `wordpress`

Both `mysql` and `wordpress` are support MySQL. But `mysql` uses [illuminate/database](https://github.com/illuminate/database) package to works with MySQL, whilst `wordpress` use native WordPress `$wpdb` object. So there are some pros and cons:

**mysql**: requires PHP 5.4+ and running `composer update` but more powerful, works with any application. Don't worry, composer is easy to use.

**wordpress**: You can run it without configuration, but only works with WordPress.

You can use `mysql` storage driver for all app including WordPress but cannot use `wordpress` for any app.

## Using MySQL Storage Driver

1. Open `config.php`
    - Change `storage_driver` to `mysql`
    - In `mysql` section, enter your database connection info.

1. Import `vendor/gigaai/schema/mysql.sql` to your database, this will setup db tables for you. If you want to set table prefix, please edit that file manually before importing.

### Database Queries

All drivers have same methods, see [Storage Basic](/docs/standalone/storage) for more detail. Since `MySQLStorageDriver` use `illumunate/database` package. It has even more methods. To make a database query, use `$bot->storage->db()` method. It will returns Laravel `\DB` instance: 

For example:

```
$bot->answers('check my license', 'Please enter your license key')->wait('key');

$bot->answer('@key', function ($bot, $user_id, $input) {
    
    $user_exists = $bot->storage->db()->table('users')->where('license_key', $input)->exists();
    
    if ($user_exists)
        $bot->say('Your license is valid');
    else
        $bot->say('Your license is invalid');
});
```

For `illuminate/database` usage, please check it on [Laravel Documentation](https://laravel.com/docs/5.0/queries)