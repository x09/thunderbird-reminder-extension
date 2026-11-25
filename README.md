# Email Reminders for Thunderbird

**English** · [Русский](README.ru.md)

Set reminders on email messages and receive a desktop notification when they are due.
This is the [x09 fork](https://github.com/x09/thunderbird-reminder-extension) of
[Marek Hajduczenia's original project](https://github.com/gitzone83/thunderbird-reminder-extension),
with Russian localization and an infrastructure for additional languages.

## What this fork adds

- Complete **English and Russian** catalogs: 98 messages per language, covering
  all four pages, menu items, notifications, errors, confirmations and tag labels.
- Automatic language selection from the Thunderbird UI, with English as the fallback.
- Locale-aware dates and relative times, including Russian grammatical forms.
- A shared localization helper, catalog validation and a [translator guide](LOCALIZATION.md).
- Translation of the managed reminder tag when the UI language changes, while
  preserving custom tag names, tag keys and colors.
- Wrapping for longer controls and a snooze menu that stays inside the scrollable popup.
- A reproducible XPI builder and automated checks, without third-party runtime dependencies.

The implementation is in this fork's `master`. The localization contribution is
also proposed upstream in [PR #6](https://github.com/gitzone83/thunderbird-reminder-extension/pull/6).
That PR has its own status; this fork can be built and used independently.

The source manifest version is **0.3.1**. The separately built localization XPI
uses **0.3.1.1** via a build-time override; it is not an official upstream release.

## Features

- Set a reminder from an email's right-click menu, with a date/time and optional notes.
- Use quick choices for one hour, four hours, tomorrow at 09:00 or next week.
- Identify emails with active reminders by the orange **Has Reminder** tag.
- View active reminders from the toolbar, or open the full list and filter by status.
- Snooze, complete, dismiss, delete or reactivate reminders.
- Export/import reminders as JSON and optionally archive an email after setting a reminder.
- Keep reminder data locally. See [PRIVACY.md](PRIVACY.md).

## How notifications actually work

Thunderbird must be running. The extension checks for due reminders **once per
minute**, so a notification may appear on the next check rather than at the exact
scheduled second. It also checks overdue reminders on application startup.

A due pending/snoozed reminder produces a **system desktop notification** with a
title, email subject and sender. Its location, appearance, duration and notification
history depend on the operating system and desktop environment. Clicking it attempts
to open the original email in Thunderbird.

After the notification API call succeeds, the reminder changes to `notified`
(**Due** in English; **Срок наступил** in Russian). This records that the notification
was requested; it does not prove that the user saw it. The same reminder is **not
shown repeatedly**. Use **Snooze** to schedule another notification.

There is no persistent reminder dialog or extension-defined sound. A system sound,
if any, depends on desktop settings. If Thunderbird is closed at the due time,
notification delivery waits until it runs again.

The toolbar badge displays `pending|due`: pending includes snoozed reminders;
due counts reminders already marked `notified`. A red/overdue date is a time-based
visual indicator, not proof that a notification was shown. Reopen the popup or
list to refresh it when checking status.

If no notification appears, check the reminder's **Status** in the full list,
Thunderbird's system notification permissions, and Do Not Disturb. An already
notified reminder needs to be snoozed before another delivery. Completed and
dismissed reminders can be reactivated.

## Languages

The interface follows the Thunderbird UI language. Restart Thunderbird after
changing that language. Unsupported languages fall back to English messages;
date/time formatting still uses the UI locale. Email subjects, senders, notes,
internal status values and stored timestamps are not translated.

To add a language, copy `_locales/en/messages.json` to `_locales/<locale>/messages.json`,
translate the messages while retaining keys and placeholders, then run the
catalog validator. See [LOCALIZATION.md](LOCALIZATION.md) for the complete workflow.

## Build and install this fork

Requirements: Git and Python 3 to build; Node.js 18+ for the checks.

```sh
git clone https://github.com/x09/thunderbird-reminder-extension.git
cd thunderbird-reminder-extension

node scripts/check-locales.mjs
node --test tests/i18n.test.cjs
python3 scripts/build-xpi.py --version 0.3.1.1
```

Install `dist/email-reminders-0.3.1.1.xpi` in Thunderbird:
**Add-ons and Themes → gear icon → Install Add-on From File**.
The builder includes runtime files and the license; it excludes screenshots,
tests, documentation and Git metadata. Omitting `--version` uses the manifest version.

The add-on ID remains `email-reminders@mhajduczenia.dev`: this replaces the same
add-on rather than installing a second independent copy. Reminder data is not
cleared by the localization changes. Export a backup before replacing an existing installation.

For development, use **Debug Add-ons → Load Temporary Add-on** and select
`manifest.json`. The upstream add-on store listing is a separate distribution;
it does not establish which changes from this fork it includes.

## Validation and current limitations

- Catalog/reference checks and 8 Node tests passed.
- 12 browser smoke scenarios covered four pages in English, Russian and an
  unsupported locale, using mocked Thunderbird APIs.
- Local XPIs installed and activated in isolated Thunderbird 159 profiles;
  Russian, English and English fallback selection were verified.
- A comparative notification test of the original and localized builds produced
  desktop notifications in ALT Workstation 11.2 / Thunderbird 159 / KDE.

The manifest declares Thunderbird **106+**, but compatibility testing here used
**159**. Earlier versions and a complete real-mailbox workflow remain to be checked.

Two inherited settings limitations remain: the background check interval is
hardcoded to one minute despite the interval selector, and day-based quick
choices/reactivation use 09:00 despite the default-time setting. Localization
has not changed this scheduling logic. Recurring reminders are not implemented.

## Screenshots: original upstream interface

The images below are retained from the original project. They illustrate the
workflow, **not the current Russian interface**. Layout and text may differ from
this fork, and the desktop notification's appearance is platform-specific.
No current Russian screenshots are published here yet.

<details>
<summary>View original English screenshots</summary>

### Create a reminder

![Original: context menu](screenshots/context-menu.png)
![Original: reminder dialog](screenshots/reminder-dialog.png)

### Tags and toolbar

![Original: email tag](screenshots/email-with-tag.png)
![Original: toolbar badge](screenshots/toolbar-badge.png)
![Original: toolbar popup](screenshots/toolbar-popup.png)

### Full list, notification and settings

![Original: reminder list](screenshots/reminder-list.png)
![Original: desktop notification — platform-specific appearance](screenshots/notification.png)
![Original: settings](screenshots/settings.png)

</details>

See the [screenshot plan](screenshots/README.md) for replacing these examples with
current Russian and English captures using demonstration mail.

## Contributing and license

Translation improvements, bug reports and reproducible test cases are welcome.
Send fork-specific changes to this repository; discuss upstream contributions in
the [original project](https://github.com/gitzone83/thunderbird-reminder-extension).

MIT license; see [LICENSE](LICENSE). Original extension by Marek Hajduczenia.
Built with the [Thunderbird MailExtensions API](https://webextension-api.thunderbird.net/).
