# Changelogs
---
## Version 2.2 - Chiba (January 02nd, 2017)
- New: Account Linking
- New: List message type
- New: Auto Stop (Mute) bot
- New: Whitelisted domains
- Improvement: Allows user remove subscribers from channels.
- Improvement: Don't response message echo
- Improvement: Better Message code structure
- Improvement: Better button sanitizer
- Improvement: When notification message limit is set to 0. You can send unlimited messages.
- Improvement: Add soft delete for all db tables.
- Improvement: Add creator_id field to some db tables
- Improvement: You can set intended action for notification.
- Fix: Storage::set() doesn't works with meta data

## Version 2.0.2 (November 10th, 2016)
- Improvement: Better UTF-8 support 
- Improvement: Add default seeder for GIGA_GET_STARTED_PAYLOAD
- Fix: Quick Replies doesn't works inside closure
- Change: Use MySQL REGEX or LIKE syntax for Text Matching
- Under the hood: Move Messenger Bot answer(), answers(), say(), says(), wait(), then() methods to LearnTrait.

## Version 2.0.1 (October 28th, 2016)
- Fix: Quick Replies and Default answers doesn't works
- Improvement: URL should be URL instead of force to File
- Change: Default channel in example file is 1 instead of 2.

## Version 2.0 (October 25th, 2016)
- New: Subscription feature
- New: Fluent intended action
- Improvement: Performance now 5X faster
- Improvement: Split index.php to index.php, seeder.php, subscription.php
- Improvement: Quick Replies can works with multiple messages
- Improvement: User can use either $bot->say() or return statement in callback
- Fix: Cannot handle quick replies payload
- Change: Add more tables and fields to database
- Change: Remove File Storage Driver
- Change: Remove WP Storage Driver

## Version 1.1.1 (September 14th, 2016)
- Improvement: `MySQLStorageDriver` is shipped with the package by default
- Improvement: Attachment now works with Intended Actions
- Improvement: Remove `$bot->run();` method on `public/index.php`
- Fix: `Driver Not Found` exception in strict mode

## Version 1.1 (August 30th, 2016)
- New: Add Attachment Handler
- New: Add MySQLStorageDriver and WordPressStorageDriver
- Improvement: Callback now takes up to 3 arguments: `$bot`, `$user_id`, and `$input`
- Improvement: Use `?subscribe` instead of `/subscribe.php`
- Fix: `$bot->say()` method doesn't works with two levels array generics and buttons
- Fix: Text Matching when `foo` works same as `%foo`

## Version 1.0.1 (August 13th, 2016)
- New: Quick Replies
- Improvement: Temporary remove Auto Stop feature since this makes people feel complicated
- Improvement: Add PHPUnit test suite
- Fix: Intended Actions loop or sending only 1 time.
- Fix: User can't set question mark in their pattern

## Version 1.0 (Jul 21st, 2016)
- Initial Release