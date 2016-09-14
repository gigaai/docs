# Upgrade Guide
---

## Upgrading to 1.1.1 from 1.1

- Make sure your server is running PHP 5.4+
- Override whole project with new files, except `config.php`
- Open `/public/index.php` and remove the last `$bot->run();` call

**My Server is Running PHP 5.3**

If your server is running PHP 5.3, you should consider upgrade to PHP 5.4+. If you cannot upgrade and still want to use outdated version, you cannot use `MySQLStorageDriver`. Here is the instruction how to use Giga AI on PHP 5.3:

- Do above steps
- Replace your `composer.json` with new content:
```
{
        "require": {
            "gigaai/framework": "dev-master"
        }
}
```
- Run `composer update`

## Upgrading to 1.0.x to 1.1

- Override whole project with new files, except `/public/index.php` and `config.php`
- Remove `/public/subscribe.php`
- If you use `mysql` storage driver, add these lines to `config.php`:

```
'mysql' => [
    'host'      => 'localhost',
    'database'  => 'YOUR_DATABASE_NAME',
    'username'  => 'YOUR_DATABASE_USERNAME',
    'password'  => '',
    'charset'   => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix'    => '',
],
```

