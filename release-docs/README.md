# Документы к текущей .app / Documents for the current .app

## Русский

Комплект относится к одной универсальной `Программа скачивания.app` с `yt-dlp` 2026.08.19, FFmpeg/ffprobe 9.0.2 Martin Riedl, Deno 2.9.7 и Bellota Bold.

- [LICENSE](LICENSE): Лицензия некоммерческого использования 1.0 для оригинального кода приложения и документации, Copyright (c) 2026 OzzyLabz.
- [SOURCE_REFERENCES.md](SOURCE_REFERENCES.md): происхождение файлов, контрольные суммы, ссылки на исходники.
- [THIRD_PARTY_LICENSES.txt](THIRD_PARTY_LICENSES.txt): полный опубликованный перечень уведомлений упакованного yt-dlp этой версии; собранные тексты FFmpeg, его установленных библиотек, Deno, V8, TypeScript и Bellota.
- [ffmpeg-amd64-versions.txt](ffmpeg-amd64-versions.txt) и [ffmpeg-arm64-versions.txt](ffmpeg-arm64-versions.txt): неизменённые данные поставщика для конкретных выпусков.

При передаче сохраняйте всю папку рядом с `.app` в одном DMG. Дополнительные документы не требуют пересборки приложения. Собственный код приложения и документация охватываются [LICENSE](LICENSE); сторонние компоненты сохраняют свои условия.

В перечень не добавлены зависимости, найденные только в общем Cargo.lock Deno: это не доказательство их включения в исполняемый файл. SDL из версии поставщика FFmpeg относится к его общему комплекту; `ffplay` в нашей `.app` отсутствует.

### Условия для вложенных файлов

| Файл/компонент | Разрешение и условия |
| --- | --- |
| `yt-dlp` | Unlicense собственного кода yt-dlp допускает использование и распространение. Готовый `yt-dlp_macos` содержит компоненты с другими лицензиями: полный официальный файл уведомлений сохранён; к ним применяются их собственные условия, включая требования об исходниках там, где они предусмотрены. |
| `ffmpeg`, `ffprobe` | Использованные сборки сообщают GPLv3 или новее. Распространение допускается при выполнении GPL, включая сохранение уведомлений/лицензии и доступ к соответствующим исходникам с необходимыми скриптами сборки. |
| `deno` | MIT допускает использование, изменение и распространение с сохранением уведомления автора и текста разрешения. У вложенных компонентов собственные условия. |
| Bellota Bold | SIL OFL 1.1 допускает включение шрифта в приложение с сохранением уведомления и лицензии. Шрифт нельзя продавать отдельно; ограничения имён при изменении шрифта указаны в OFL. Шрифт не изменялся. |

Эти условия действуют и при бесплатной некоммерческой публикации. Коммерческое использование оригинального кода приложения и документации требует отдельного письменного разрешения по [LICENSE](LICENSE).

## English

This collection describes the existing universal `Программа скачивания.app`: yt-dlp 2026.08.19, Martin Riedl FFmpeg/ffprobe 9.0.2, Deno 2.9.7 and Bellota Bold.

SOURCE_REFERENCES.md records provenance, hashes, source links and supplier build scripts. THIRD_PARTY_LICENSES.txt preserves the complete upstream yt-dlp packaged-executable notices for this version and collects identified FFmpeg/library, Deno, V8, TypeScript and Bellota texts. The two FFmpeg version files are unmodified supplier records.

Keep this entire directory next to the app in the same DMG. Adding these external documents does not require rebuilding the app. The original app code and documentation are covered by [LICENSE](LICENSE), Noncommercial Use License 1.0, Copyright (c) 2026 OzzyLabz. Third-party components retain their own terms.

Dependencies found only in Deno's general Cargo.lock are excluded. SDL appears in the supplier's broader FFmpeg inventory; our app does not distribute ffplay.

### Terms for bundled files

| File/component | Permission and conditions |
| --- | --- |
| `yt-dlp` | The Unlicense permits use and distribution of yt-dlp's own code. The packaged macOS executable includes components under other licenses: the complete upstream notice file is retained, and their own terms apply, including source requirements where applicable. |
| `ffmpeg`, `ffprobe` | These builds report GPLv3 or later. Distribution is permitted subject to GPL obligations, including retaining notices/license and providing access to corresponding source and required build scripts. |
| `deno` | MIT permits use, modification and redistribution with the copyright and permission notice retained. Incorporated components have their own terms. |
| Bellota Bold | SIL OFL 1.1 permits bundling the font with the app while retaining copyright and license. Standalone sale of the font is prohibited; name restrictions for modified fonts follow OFL. The font was not modified. |

Free, noncommercial publication still follows these terms. Commercial use of the original app code and documentation requires separate written permission under [LICENSE](LICENSE).
