# Changelogs
---
## Version 2.2.1 - January 14th, 2017
- Improvement: Add jQuery maskedinput for datetime field.
- Improvement: Don't load plugin assets on other pages.

## Version 2.2 (Chiba) - January 3rd, 2017
- New: Subscription & Notification Builder.
- New: Node Stream. You can update leads automatically via Bot Builder.
- New: Session management.
- New: Support German. Credit: [Thomas Sator](https://m-factory.de).
- Improvement: Tweak the Bot Builder UI.
- Improvement: Use `Session::flash()` for better  display messages.
- Improvement: Add `creator_id` field to data tables.
- Fix: `Storage::set()` method doesn't works with meta data.

## Version 2.1 (Yanoda) - December 12th, 2016
- New: Account Linking.
- New: List message type.
- New: Add Auto Stop feature back.
- New: [random-text] shortcode.
- New: Whitelisted Domains.
- New: More properties for Buttons.
- Improvement: Switch the Click dropdown to Autocomplete.
- Improvement: Add default message for Get Started button.
- Improvement: Update the core parser.
- Improvement: Tweak the Live Preview and Conversation UX.
- Improvement: Only allows add Quick Replies in the last answer of Node.
- Improvement: Improve the Settings UI and performance, only save value of fields in active tab.
- Improvement: Better Button sanitizer.
- Improvement: Use curl instead of `file_get_contents`.
- Fix: Do not response message echo.

## Version 2.0.1 - November 7th, 2016
- Fix: Error when collation isn't UTF-8.

## Version 2.0 - November 3rd, 2016
- New: CRM Module. Seamless way to works with your Leads.
- New: Dynamic Shortcode. Helps you integrate with your posts easily.
- New: Live Preview Builder.
- New: Persistent Menu Builder.
- New: Call Button on Builder.
- New: Quick Replies on Builder.
- New: Tag and Search Nodes.
- New: Subscription API.
- Change: `fmb_pre_run` now becomes `giga_pre_seed`.
- Change: User framework v2.
- Improvement: Performance now 2x faster.

## Version 1.0 - May 1st, 2016
- Initial Release.