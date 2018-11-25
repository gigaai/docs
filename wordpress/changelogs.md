# Changelogs
---
## Version 3.0. - October 25th, 2018
This version is totally breaking changes, please refer to [Upgrade Guide](/docs/wordpres/upgrade) before upgrade.

- Breaking changes: API, Interface, PHP version support, and Database.
- New: Facebook SDK and App Integration.
- New: Better Multiple Pages support. You can now select pages from dropdown instead of manually enter page id and access token.
- New: Support Facebook NLP.
- New: Facebook Login and Profile Connect
- New: WYSIWYG instead of Live Preview Bot Builder interface.
- New: Support all latest Messenger Platform features.
- New: Facebook Broadcasts & Labels (Channels) feature for faster messeage sending.
- New: Batch messages for better performance.
- New: Redesigned CRM.
- New: Auto Stop and replaced by Handover Protocol. More convenience way for team working.
- New: Typing Indicator API and message type.
- New: Import/Export templates.
- New: Permissions management.
- New: Soft deletion is not implemented for all modules.
- New: NLP shortcode, all lead profile fields can become shortcode and easier way to add shortcode. The shortcode now has ability to update lead also. And, shortcodes work in any message types at any position (for example: buttons, bubble title...)
- New: Method resolver for callback function in `$bot->answers()` method, you don't have to remember variables position.
- New: LightKit integration.
- New: ParcelJS and NodeJS integrated for more convenience way to code.
- Huge Improvement: We use Facebook batch messages for all messages which helps you got 4x performances than other scripts.

## Version 2.3.1 - May 08th, 2017
- Improvement: Only cache the payload if it's postback.
- Improvement: Add Cancel button next to Save Changes in Bot Builder.
- Improvement: Clear Messenger Profile cache after update.
- Improvement: List can only add 1 last button.
- Fix: Migration error in MySQL strict mode.
- Fix: Quick replies doesn't show.
- Fix: Plugin typos.

## Version 2.3 (Frankfurt) - April 22nd, 2017
- New: Multiple Pages (Premium).
- New: Replace Thread Settings with new Messenger Profile.
- New: Bot now can update lead based on their sent data via Builder.
- New: Logger module.
- New: `$bot->release()` method which lets you validate and forget intended actions. 
- Improvement: Bot Builder responses can now draggable.
- Improvement: Search and Filter in CRM.
- Improvement: You can now use text matching and get `$input` variable for payload.
- Improvement: `$bot->answer()` now can takes 3 arguments, the third arguments is the node attributes.
- Improvement: Support using icon in quick replies.
- Fix: All known CSS bugs and typo.
- Fix: Cannot save notification when `end_at` field is null.

## Version 2.2.4 - March 26th, 2017
- Improvement: Remove tooltip() method
- Fix: DB Migration doesn’t works with old MySQL version

## Version 2.2.3 - March 08th, 2017
- Improvement: Better compatibility with some shared hosts.
- Improvement: Update `gigaai/framework` to the latest version.
## Version 2.2.2 - January 26th, 2017
- New: You can use `tax` parameter in [post-generic] shortcode

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