# Stream Arc W9 Pro firmware updates

Public release feed for the Stream Arc updater on Eweat W9 Pro / S905X5M devices.

`latest.json` stays disabled until a signed Android 14 virtual A/B OTA is tested on the exact hardware. No firmware release is available yet.

The updater shows change notes, Update now, Remind later (24 hours), and Skip this release. Devices need no GitHub token.

## Publishing

1. Build a signed Android 14 virtual A/B OTA with the device's accepted OTA key and configuration.
2. Test boot, remote controls, playback, update installation, and slot recovery on the box.
3. Upload `payload.bin` and `payload_properties.txt` to a GitHub Release. The Amlogic burning `.img` is not an OTA payload.
4. Run the supplied `publish_feed.py` with release notes, exact source build fingerprints, increasing version code, and `--device-tested`.
5. Confirm the release assets work anonymously, then publish the generated `latest.json` on `main`.

The current test-firmware baseline is version code `20001`. Future firmware must update `ro.streamarc.version_code` and `ro.streamarc.version`. Android update_engine validates payload signatures; reboot requires user confirmation after installation.

Keep private signing keys out of this repository.
