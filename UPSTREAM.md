# Upstream base / Исходная версия

The x09 fork 0.4.0.1 is based on the official Thunderbird Add-ons 0.4.0 package:

- [Original XPI](https://addons.thunderbird.net/user-media/addons/989326/email_reminders-0.4.0-tb.xpi)
- SHA-256: `47aaf518761d53f195a60f22edcf9f70d1e56b4258c6bc27ca6fb1f6769e39fe`
- Compared on 2026-11-27 with upstream Git commit
  `64a6072c58b193a2e5adfd316c5b4dd8a3727e73`.

Every packaged file was compared byte-for-byte against that Git commit (ZIP
signature metadata is excluded). Only `manifest.json`, `CHANGELOG.md` and
`RELEASE_NOTES.md` differ. The manifest differs only in version (0.3.1 → 0.4.0).
JavaScript, HTML, CSS, icons, English catalog and LICENSE are identical. In
particular, optional archiving and its permission were already in the Git base.
The official package's changelog dates 0.4.0 to 2026-04-28; the date shown by
Thunderbird as “Last Updated” is not evidence of its store publication date.

The fork retains our localization, tag handling and layout changes, build and
verification tools, bilingual documentation and separate add-on identity. The
upstream release notes are retained below the fork notes. Original licensing and
copyright attribution remain intact. The upstream store signature is not reused.

## Русский

Основа форка 0.4.0.1 — официальный XPI 0.4.0 по ссылке выше. Проверка всех файлов
пакета показала, что программный код совпадает с исходной базой наших изменений.
Различаются только номер версии в манифесте и два документа о выпуске. Поэтому
перенос не требует повторного изменения логики: сохранены наши русский и английский
интерфейсы, работа с метками, исправления вёрстки, инструменты, документация и
отдельный идентификатор форка. Архивирование из 0.4.0 также сохранено.

С версии форка 0.3.2 можно обновиться установкой нового XPI поверх старого:
идентификатор не изменился, напоминания и настройки сохраняются. Переход с
оригинала или 0.3.1.1 требует экспорта и импорта JSON, как описано в README.ru.md.
