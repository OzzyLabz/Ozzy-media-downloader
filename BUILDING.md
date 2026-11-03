# Building the universal macOS app

[Русский](BUILDING.ru.md) · English

`build.sh` builds the project without an `.xcodeproj`. You need macOS with Apple Command Line Tools (`xcrun swiftc`, `lipo`, `codesign`), `zsh`, and the input executables for both architectures. The script creates one `dist/Программа скачивания.app`: it compiles the app separately for `x86_64` and `arm64`, then merges the results with `lipo`. It also merges `ffmpeg`, `ffprobe`, and `deno`. The already universal `yt-dlp_macos` is copied as `yt-dlp`.

## Input files

Place the verified executables in a separate tools directory:

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

The local build used `yt-dlp_macos` 2026.08.19, FFmpeg/ffprobe 9.0.2 from Martin Riedl, and Deno 2.9.7. Check architectures, minimum macOS versions, archive checksums, and license terms before replacing an executable. These input files are not in the project tree. By default, the script looks in `/private/tmp/media-downloader-universal-inspect`; set `MEDIA_TOOL_SOURCE_DIR` to use your own directory.

The current FFmpeg/ffprobe executables do not need replacement solely because of the GPL/OpenSSL flags: this build uses OpenSSL 3.6.4. The supplier's FFmpeg 9.0.2 develop scripts and release version inventories have been found. See [release-docs/SOURCE_REFERENCES.md](release-docs/SOURCE_REFERENCES.md) for the exact downloads, hashes, source references and supplier build scripts, and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for licensing status. Keep `release-docs/` with the binary archive; adding these external documents does not require rebuilding the app.

## Build and check

From the `универсал` directory, run:

```sh
MEDIA_TOOL_SOURCE_DIR="/path/to/tools" zsh build.sh
```

The script overwrites `dist/Программа скачивания.app` and working files in `/private/tmp/media-downloader-universal-build`. It signs the bundled tools and app ad hoc; it does not use Developer ID or notarization.

Check the result:

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

All five executables should report `x86_64 arm64`; both slices of the main executable should report `minos 13.0`. These checks do not replace a launch and test download on Intel and Apple Silicon Macs running the required OS versions.

After the distribution requirements and release checks are complete, create the DMG with one command (it uses the app from the working folder and `dmg/background.png`):

```sh
./make-dmg.sh
```

## License files

The app's original code and documentation are covered by [LICENSE](LICENSE), Noncommercial Use License 1.0, Copyright (c) 2026 OzzyLabz. Preserve the copy in [release-docs/LICENSE](release-docs/LICENSE) when creating the DMG. Bundled tools retain their own licenses and source obligations. The license files are external documents and do not require rebuilding the app.
