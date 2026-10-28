# Publication notice — Ulefone GQ5012BF1 board source mirror (partial)

This is a **sanitized, partial** C48 provenance mirror of the Ulefone-specific
source in the LieppOS GQ5012BF1 combined kernel tree. It is not a build root and
not a complete device-support drop.

## Source

- Kernel publication commit: `d0feaaee4484e2fdd5cd87ebbf4c9e273a50b8b0`
- Kernel publication tree: `5b87650c888eab5b14925e7799ec900d4f94f307`
- C47 local import commit (not published): `7a75e19ebf5d7e4b3876c19f4e77cad385dff4f0`
- C44/C45/C46 source lineage: `ce07b664` + `d02a8942` + `2c896fab`

## Withheld in C48

| Path | Embedded material |
| --- | --- |
| `drivers/input/touchscreen/focaltech_touch/` | 118,972-byte stock FT3680 firmware extracted from a vendor `.ko`; `focaltech_flash.h` has no GPL grant |
| `drivers/input/touchscreen/hynitron/` | `firmware_cst816t.inc` and `firmware_cst8xx.inc` controller firmware |
| `drivers/misc/mediatek/tiny_lcd/` | 1.4 MB vendor logo and LCD init arrays |
| `drivers/power/supply/sh366003/` | Stock SinoWealth AFI/calibration image |

These files remain in the canonical kernel tree for private builds. They are
not redistributed until the owner obtains or documents redistribution rights.
The mirror is partial by design; do not describe it as complete board support.

## Licensing

GPL-2.0 is dominant. Per-file SPDX identifiers and original notices are
preserved. Files without an SPDX header are not relicensed by LieppOS. No
private key, signing secret, firmware image or calibration blob is included in
this publication.
