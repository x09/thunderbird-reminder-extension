# Screenshot provenance and replacement plan / План обновления скриншотов

## Current images / Текущие изображения

The PNG files in this directory and `originals/` were inherited from the upstream
project. They show its English UI. They have not been regenerated for the localized
fork. Both READMEs label them as upstream examples. Keep the files and their paths
until current captures are ready; do not overwrite them with edited translations.

PNG-файлы в этой папке и `originals/` получены из исходного проекта и показывают
его английский интерфейс. Они не переснимались для локализованного форка.
В обоих README они обозначены как примеры оригинала. Пока новые снимки не готовы,
сохраняем файлы и пути. Не заменяем английские подписи русскими в графическом редакторе.

## Proposed capture set / Предлагаемый набор

| Screen / Экран | What to show / Что показать |
| --- | --- |
| Context menu / Контекстное меню | Set Reminder / Установить напоминание |
| Creation dialog / Создание | Date, quick choices and a demonstration note / Дата, быстрый выбор и учебная заметка |
| Email tag / Метка письма | Has Reminder / Есть напоминание |
| Toolbar popup / Всплывающая панель | Pending and due reminders, badge, expanded snooze choices / Ожидающие и сработавшие записи, счётчик, открытое меню отсрочки |
| Full list / Полный список | Different statuses and the overdue date / Разные статусы и просроченная дата |
| Settings / Настройки | All current controls; retain the documented scheduling limitations / Все текущие настройки с сохранением оговорок об ограничениях |
| Desktop notification / Системное уведомление | Actual desktop banner, with its platform named / Настоящее уведомление с указанием платформы |

## Capture and publication / Съёмка и публикация

1. Use a separate Thunderbird test profile and demonstration mail with invented
   names/addresses, such as `sender@example.invalid`. Do not expose real mailbox data.
2. Capture the installed XPI in both UI languages. Proposed new paths:
   `screenshots/ru/` and `screenshots/en/`, retaining stable descriptive file names.
3. Record the XPI version, Thunderbird version, operating system, desktop environment,
   UI language and capture date for each set. Native notification appearance must
   be described as platform-specific, not universal.
4. Lead the Russian README with Russian captures and the English README with English
   captures. Keep original examples in a separate collapsed historical gallery.
5. Browser-test captures can supplement UI documentation only if explicitly labeled
   as a test preview with mocked APIs. They cannot substantiate actual mail integration
   or native notification delivery.

Снимаем установленное расширение в отдельном профиле Thunderbird на вымышленных
письмах. Планируем отдельные папки `ru/` и `en/`. Для каждого набора фиксируем версии
XPI и Thunderbird, ОС, окружение рабочего стола, язык и дату съёмки. В русский README
помещаем русские снимки, в английский — английские; исходные примеры оставляем в
сворачиваемом архивном разделе. Снимок уведомления KDE подписываем именно как KDE.
Браузерные тестовые изображения допустимы только с явной пометкой о тестовых API
и не заменяют проверку уведомлений в настоящем Thunderbird.

This is a plan; no new screenshot files have been added yet.
Это план: новые скриншоты пока не добавлены.
