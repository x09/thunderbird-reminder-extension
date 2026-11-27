# Release Notes: x09 fork 0.4.0.1

Based on the official 0.4.0 XPI, with our English/Russian localization and fork
identity preserved. See [UPSTREAM.md](UPSTREAM.md) for the comparison and
[README.md](README.md) / [README.ru.md](README.ru.md) for installation and migration.

Install over fork 0.3.2 to retain reminders and settings. Users of the original
add-on or fork 0.3.1.1 must export JSON, disable the old add-on, install this fork
and import their reminders. Future fork updates are installed manually.

---

## Original upstream release notes

# Release Notes: v0.4.0

## What's New in v0.4.0

### Archive on Reminder (New!)
A frequently requested option: keep your inbox tidy by automatically archiving emails as soon as you set a reminder on them.

- New **"Archive email after setting a reminder"** checkbox in Settings → Inbox Behavior
- **Off by default** — opt in when you want it
- Uses Thunderbird's built-in archive (your per-account Archives folder, with whatever year/month structure you've already configured)
- The reminder remains fully trackable via the popup, reminder list, and notifications
- Clicking a reminder still opens the original email, even after it has been archived

## New Permissions

This version requires one additional permission:
- **messagesMove** — required by Thunderbird's `messages.archive()` API. Used only when the new "Archive email after setting a reminder" option is enabled. No data is transmitted externally.

## Previously in v0.3.x

- Visual "Has Reminder" tag on emails with active reminders
- Toolbar badge with pending/due reminder counts
- Reminder counts in popup header

## Requirements
- Thunderbird 106 or later
