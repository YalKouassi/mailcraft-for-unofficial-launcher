# MailCraft for Craft Unofficial Launcher

**An unofficial mirror** of [MailCraft](https://github.com/UCS-Care-Group/mailcraft) releases, maintained by
[YalKouassi](https://github.com/YalKouassi), so that
[Craft Unofficial Launcher](https://github.com/YalKouassi/craft-unofficial-launcher) can install
and update MailCraft.

This repo is **not affiliated with, endorsed by or supported by UCS Care Group** (the authors of MailCraft),
**or by ArtCraft**. Report problems with MailCraft itself upstream at
<https://github.com/UCS-Care-Group/mailcraft>; report problems with this mirror here.

## What this repo publishes

The packages in this repo's releases are **MailCraft's own builds**, as published on
[UCS-Care-Group/mailcraft's releases](https://github.com/UCS-Care-Group/mailcraft/releases). Nothing is rebuilt and no program file is
changed. Each release here:

- downloads upstream's packages and verifies each one before using it;
- renames them to the launcher's `<id>-<version>-<os>-<arch>` naming and, only where the launcher
  couldn't install an archive's layout, repacks that archive (the same files with the same bytes,
  in different folders);
- adds `craft-app.json`, the icon, `SHA256SUMS.txt`, and upstream's licence files from the same tag.

The notes of each release list every file, the upstream asset it came from, its SHA-256, and
whether it was repacked, so you can compare it with upstream's release.

### For MailCraft

Upstream already names its packages the way the launcher expects, and its portable zips and
tarballs already have the right layout, so every package is mirrored **byte for byte under the
same name**. Each one is checked against upstream's `SHA256SUMS.txt` before it is mirrored.

Not mirrored: the AppImage `.zsync` delta files, `*.intoto.jsonl` provenance, `SHA256SUMS.txt.sig`, and the CLI-only (`mailcraft-cli-*`) and web (`mailcraft-web-*`) builds.

## How it runs

[`.github/workflows/bridge.yml`](.github/workflows/bridge.yml) runs every 30 minutes. It uses
[craft-bridge](https://github.com/YalKouassi/craft-bridge) with [`bridge.toml`](bridge.toml) to
check upstream's latest release and mirror it if this repo doesn't have it yet. If upstream starts
publishing its own `craft-app.json`, the bridge stops publishing, and the launcher should point at
upstream directly.

Using this mirror means trusting its maintainer as well as upstream; see
[craft-bridge's Trust section](https://github.com/YalKouassi/craft-bridge#trust).

## Licences

MailCraft is licensed by its authors under Apache-2.0 OR MIT (with a NOTICE file); each release attaches upstream's licence files.
This repo's own files (the config, workflow and this README) are available under MIT OR
Apache-2.0 ([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)).
