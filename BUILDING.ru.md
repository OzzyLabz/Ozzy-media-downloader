# Сборка универсальной версии для macOS

[English](BUILDING.md) · Русский

Проект собирается скриптом `build.sh` без файла `.xcodeproj`. Нужны macOS с Apple Command Line Tools (`xcrun swiftc`, `lipo`, `codesign`), `zsh` и входные бинарники для обеих архитектур. Скрипт создаёт одну `dist/Программа скачивания.app`; основная программа компилируется отдельно для `x86_64` и `arm64`, затем объединяется через `lipo`. Вложенные `ffmpeg`, `ffprobe` и `deno` объединяются тем же способом. Готовый универсальный `yt-dlp_macos` копируется как `yt-dlp`.

## Входные файлы

Поместите проверенные бинарники в отдельный каталог инструментов со следующими именами:

```text
<tools>/
  yt-dlp_macos
  riedl-x64/ffmpeg
  riedl-x64/ffprobe
  riedl-arm64/ffmpeg
  riedl-arm64/ffprobe
  deno-x64/deno
  deno-arm64/deno
```

У использованной локальной сборки версии: `yt-dlp_macos` 2026.08.19, FFmpeg/ffprobe 9.0.2 (сборка Martin Riedl), Deno 2.9.7. Сверяйте архитектуры, минимальную версию macOS, контрольные суммы архивов и лицензионные условия при замене любого бинарника. В текущем дереве проекта этих входных файлов нет. По умолчанию скрипт ищет их в `/private/tmp/media-downloader-universal-inspect`; для своего каталога используйте `MEDIA_TOOL_SOURCE_DIR`.

Текущие FFmpeg/ffprobe не нужно заменять только из-за флагов GPL/OpenSSL: эта сборка использует OpenSSL 3.6.4. Найдены скрипты FFmpeg 9.0.2 в `develop` и данные версий обоих выпусков. Конкретные загрузки, суммы, ссылки на исходники и скрипты сборки поставщика приведены в [release-docs/SOURCE_REFERENCES.md](release-docs/SOURCE_REFERENCES.md), статус лицензий — в [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). Передавайте `release-docs/` в архиве вместе с приложением. Добавление внешних документов не требует пересборки `.app`.

## Сборка и проверка

Из каталога `универсал` выполните:

```sh
MEDIA_TOOL_SOURCE_DIR="/путь/к/tools" zsh build.sh
```

Скрипт перезаписывает содержимое `dist/Программа скачивания.app` и рабочие файлы в `/private/tmp/media-downloader-universal-build`. Он подписывает вложенные инструменты и `.app` ad hoc подписью; Developer ID и нотариализация не выполняются.

Проверьте результат:

```sh
APP="dist/Программа скачивания.app"
lipo -archs "$APP/Contents/MacOS/MediaDownloader"
lipo -archs "$APP/Contents/Helpers/ffmpeg"
lipo -archs "$APP/Contents/Helpers/ffprobe"
lipo -archs "$APP/Contents/Helpers/yt-dlp"
lipo -archs "$APP/Contents/Helpers/deno"
vtool -show-build "$APP/Contents/MacOS/MediaDownloader"
codesign --verify --deep --strict "$APP"
```

Для всех пяти исполняемых файлов ожидаются архитектуры `x86_64 arm64`; для основного файла — `minos 13.0` в обеих архитектурах. Эти проверки не заменяют запуск приложения и пробную загрузку на реальных Intel и Apple Silicon Mac с нужными версиями системы.

После выполнения условий распространения и проверки релиза DMG собирается одной командой (берёт программу из рабочей папки и `dmg/background.png`):

```sh
./make-dmg.sh
```

## Файлы лицензий

Оригинальный код приложения и документация охватываются [LICENSE](LICENSE): Лицензия некоммерческого использования 1.0, Copyright (c) 2026 OzzyLabz. При создании DMG сохраняйте копию в [release-docs/LICENSE](release-docs/LICENSE). Вложенные инструменты сохраняют свои лицензии и требования об исходниках. Эти файлы являются внешними документами и не требуют пересборки приложения.
