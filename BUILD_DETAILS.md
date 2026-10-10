# EXT4 Build Details

This document records a personal, locally built UN1CA configuration for the Samsung Galaxy A52s 5G (`a52sxq`). It is community documentation for reproducibility, not an official UN1CA release or a guarantee that the build is suitable for other devices.

## Status

- **Build:** Completed successfully.
- **Device test:** The resulting ROM was successfully tested on the author's Galaxy A52s 5G.
- **Target filesystem:** EXT4, configured as the build-system default on the `ext4-build` branch.
- **Upstream project:** [salvogiangri/UN1CA](https://github.com/salvogiangri/UN1CA), branch `sixteen`.

## Build environment

- **Host:** Windows with WSL2
- **Linux distribution:** Ubuntu 24.04.5 LTS
- **Target device codename:** `a52sxq`
- **Source firmware configuration:** `SM-S901E/TUR`
- **Target firmware configuration:** `SM-A528B/BTU`

Firmware selections are recorded for reference and may not be appropriate for another device or future build. Verify current project instructions before attempting a build or flash.

## Configuration change

In `scripts/internal/gen_config_file.sh`, the default value for `TARGET_OS_FILE_SYSTEM_TYPE` was changed from `erofs` to `ext4`.

The `ext4-build` branch contains this change. The upstream `sixteen` branch is kept separate and retains its upstream default.

## Build output recorded

The successful local build produced these files under `out/`:

- `UN1CA_3.2.1+-ed567b1b-dirty_20261009_a52sxq-sign.zip` — flashable ROM package (approximately 5.4 GB).
- `a52sxq_3.2.1+-ed567b1b-dirty-target_files.zip` — target-files archive (approximately 5.9 GB).

These are names from the author's local build. The ROM binaries are **not hosted in this repository**.

## Troubleshooting note

During the build process, stale workspace context files caused a failure. Regenerating them with the project's forced build option (`unica make_rom -f`) allowed the build to complete. When diagnosing a similar issue, inspect the actual build log and confirm the workspace's generated files and SELinux contexts before retrying; this note is not a universal fix for all build failures.

## Safety and attribution

- Follow the upstream project's current device-specific instructions and make a complete backup before flashing.
- A successful build or test on one phone does not establish compatibility with every variant, firmware base, or configuration.
- This is an unofficial personal configuration. It is not endorsed by Samsung or the upstream UN1CA maintainers.
- Preserve the upstream project's notices and applicable license terms. UN1CA is licensed under GPL-3.0; see the [upstream license](https://github.com/salvogiangri/UN1CA/blob/sixteen/LICENSE).
