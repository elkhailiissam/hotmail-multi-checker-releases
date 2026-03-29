# Releasing Builds

Published binaries belong **only** under [GitHub Releases](https://github.com/elkhailiissam/hotmail-multi-checker-releases/releases), not in commits on `main`.

## Platform Policy

- **Windows** receives all future public updates
- **macOS** is archived at `1.1.0`
- **Linux** is archived at `1.1.0`

## Asset Naming

Use this naming for the active Windows line:

- `Hotmail.Multi-Checker-2.1.0.exe`

Do not publish new macOS or Linux assets unless the platform policy changes.

## GitHub CLI Flow

Authenticate once:

```bash
gh auth login
```

Create or edit the release:

```bash
gh release create v2.1.0 --title "2.1.0" --notes-file CHANGELOG.md -R elkhailiissam/hotmail-multi-checker-releases
```

Upload the Windows asset:

```bash
gh release upload v2.1.0 "Hotmail.Multi-Checker-2.1.0.exe" --clobber -R elkhailiissam/hotmail-multi-checker-releases
```

## Checklist

1. Version in the app matches the public asset version.
2. Release notes mention Windows as the active platform.
3. macOS and Linux remain documented as archived `1.1.0` builds only.
4. Only Windows assets are attached for new releases.
5. If a ZIP archive is created, verify archive integrity before publishing.
