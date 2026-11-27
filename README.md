# Crosscheck releases

This repository holds the published builds of Crosscheck, the installer, and the manifest that the app reads to update itself. The source code lives in another repository. The website and the user guide are at https://d0whc3r.github.io/crosscheck-releases/.

## Install or update

```bash
curl -fsSL https://github.com/d0whc3r/crosscheck-releases/releases/latest/download/install.sh | bash
```

The script installs `/Applications/Crosscheck.app` on macOS on Apple silicon and the AppImage `~/.local/bin/crosscheck` on Linux on x86_64. In the app, select "Check for Updates…" in the app menu on macOS, or in Help on Linux.

Apple does not notarize the app. When you download the DMG in a browser, macOS blocks the first start. After you copy the app to Applications, run:

```bash
xattr -dr com.apple.quarantine /Applications/Crosscheck.app
```

## Files of a release

- `Crosscheck_aarch64.dmg`: the macOS disk image.
- `Crosscheck_amd64.AppImage`: the Linux app.
- `install.sh`: the installer.
- `latest.json`, `Crosscheck_aarch64.app.tar.gz`, and the `.sig` files: the updater manifest, the macOS update archive, and the minisign signatures. The app installs an update only when its signature matches the public key that the app holds.
