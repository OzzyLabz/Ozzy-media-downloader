# Ozzy Media Downloader 1.0

## Русский

Универсальное приложение для Mac с Intel и Apple Silicon. Минимальная версия системы, указанная в сборке, — macOS 13.0.

- Анализ ссылок и выбор качества MP4.
- Извлечение аудио в MP3.
- Ручные и автоматические субтитры, когда они доступны.
- Очередь загрузок с прогрессом и отменой.

Откройте DMG и перетащите «Программа скачивания.app» в папку «Программы». Приложение имеет ad hoc подпись и не нотариализовано; первый запуск может потребовать разрешения в настройках безопасности macOS.

Программа предназначена для некоммерческого использования. Продажа и использование для заработка запрещены условиями лицензии авторского кода. Сохраняйте папку release-docs из DMG: она содержит лицензию приложения, сторонние лицензии, уведомления и ссылки на исходники.

## English

A universal Mac app for Intel and Apple Silicon. The build specifies macOS 13.0 as its minimum OS version.

- Link analysis and MP4 quality selection.
- MP3 audio extraction.
- Manual and automatic subtitles when available.
- Download queue with progress and cancellation.

Open the DMG and drag «Программа скачивания.app» to Applications. The app is signed ad hoc and is not notarized; the first launch may require approval in macOS security settings.

The application is intended for noncommercial use. Selling it or using it to earn income is prohibited by the license for the author's code. Retain the release-docs directory from the DMG: it contains the application's license, third-party licenses, notices and source references.

---

## Инструкция публикации для автора / Publishing instructions for the author

### Русский

1. Создайте репозиторий в аккаунте OzzyLabz. Не выбирайте шаблон MIT или другой готовой лицензии: загрузите собственный файл `LICENSE`.
2. Загрузите `Sources/`, `Resources/`, `build.sh`, `LICENSE`, `README.md`, `README.ru.md`, `BUILDING.md`, `BUILDING.ru.md`, `THIRD_PARTY_NOTICES.md`, `RELEASE_NOTES.md`, `screenshot.png` и `release-docs/`. Готовую `.app` размещайте в Release.
3. Создайте DMG по командам в `BUILDING.ru.md`. Папка `release-docs/`, включая копию `LICENSE`, должна находиться рядом с приложением внутри DMG.
4. Создайте черновик Release с тегом `v1.0` и названием «Ozzy Media Downloader 1.0». В описание скопируйте русский и английский разделы выше, до этой инструкции.
5. Прикрепите DMG. Укажите рядом с загрузкой ссылку на `release-docs/SOURCE_REFERENCES.md` именно в теге `v1.0`, а также на `release-docs/THIRD_PARTY_LICENSES.txt` и `LICENSE`. Сохраняйте доступность соответствующих исходников и скриптов согласно условиям вложенных инструментов.
6. Проверьте содержимое DMG и ссылки перед публикацией черновика.

### English

1. Create a repository under OzzyLabz. Do not select an MIT or other license template: upload the custom `LICENSE` file.
2. Upload `Sources/`, `Resources/`, `build.sh`, `LICENSE`, `README.md`, `README.ru.md`, `BUILDING.md`, `BUILDING.ru.md`, `THIRD_PARTY_NOTICES.md`, `RELEASE_NOTES.md`, `screenshot.png` and `release-docs/`. Distribute the built `.app` through a Release.
3. Create the DMG using the commands in `BUILDING.md`. Include `release-docs/`, containing a copy of `LICENSE`, next to the app inside the DMG.
4. Create a draft Release with tag `v1.0` and title “Ozzy Media Downloader 1.0”. Copy the Russian and English sections above, before these instructions, into its description.
5. Attach the DMG. Next to the download, link to `release-docs/SOURCE_REFERENCES.md` at tag `v1.0`, `release-docs/THIRD_PARTY_LICENSES.txt` and `LICENSE`. Maintain access to corresponding source and build scripts as required by the bundled tools' terms.
6. Check the DMG contents and links before publishing the draft.
