# MorpheS

Personal fork of [Morphe Manager](https://github.com/MorpheApp/morphe-manager),
built as `app.morphe.manager.debug` and released from this repository as
`MorpheS`.

## Covers what Morphe does not ship

- Preset thumbnail previews: a patch bundle can ship images under
  `previews/<package>/<optionKey>/<value>.png` beside the bundle file or inside
  its archive; dropdown entries and the field show them beside each preset
  name. jpg, jpeg, webp and muted mp4 or webm previews work the same way, and
  still images win ties so clips stay opt in per pack. The bundle used with
  this fork documents the convention.
- Preview cache keyed by bundle file name, size and modification date, so a
  bundle update never serves art from the previous version.
- MorpheS identity: own launcher mark, own app name, updates come from this
  repository instead of upstream.

## Updates

The app self updates from this repository: a check reads the GitHub Releases
of this repo, downloads the APK attached to the latest release and installs it. A scheduled
workflow here rebases on upstream Morphe `dev` daily and publishes a release
whenever upstream moved, so upstream changes keep arriving with the fork
features intact. Version strings carry an `-s.N` suffix, and the suffix rules
the chooser: newer suffix wins.

## Building

Needs Java 21 and the Morphe registry credentials as `gpr.user` / `gpr.key`:

    ./gradlew :app:assembleDebug

Release builds sign with a personal keystore passed through
`morpheSKeystore`, `morpheSKeystorePassword` and `morpheSKeystoreAlias`.

## License and notices

Upstream [Morphe Manager](https://github.com/MorpheApp/morphe-manager) is a
GNU GPLv3 hard fork; this fork keeps their `LICENSE` and their `NOTICE` intact
and is not affiliated with the Morphe project. The MorpheS launcher mark and
name are this repository's own.
