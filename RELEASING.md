# Releasing builds

Published executables and disk images belong **only** under [GitHub Releases](https://github.com/elkhailiissam/hotmail-multi-checker-releases/releases) (**Assets**), not in commits on `main`. The `.gitignore` in this repository blocks common binary extensions to reduce accidental commits.

## Upload with GitHub CLI

Authenticate once (`gh auth login`), then attach a file to an existing release tag:

```bash
gh release upload v1.0.0 "Hotmail.Multi-Checker-1.0.0-Windows-x64-Portable.exe" --clobber -R elkhailiissam/hotmail-multi-checker-releases
```

Replace the tag and filename with your current version and artifact paths. Use `--clobber` to replace an asset with the same name.

## Checklist

- Tag matches the version in release notes and user-facing docs.
- All platforms you ship (Windows installer and/or portable, macOS `.dmg`, Linux `.AppImage`) are attached under **Assets**.
- Optional: publish SHA-256 checksums in the release description for user verification.
