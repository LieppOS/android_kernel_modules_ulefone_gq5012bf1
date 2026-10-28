# Ulefone GQ5012BF1 board source mirror

This repository holds a **sanitized, partial source mirror** of the
Ulefone-specific and board-peripheral kernel source used by the LieppOS Ulefone
Armor 29 Pro Thermal (GQ5012BF1 / MT6878T) build. It is not a standalone kernel
build root and it is not a complete device-support drop.

## Source

| Field | Value |
| --- | --- |
| Kernel repository | `android_kernel_ulefone_gq5012bf1` |
| Source commit | `d0feaaee4484e2fdd5cd87ebbf4c9e273a50b8b0` (C48 publication snapshot) |
| Source tree | `5b87650c888eab5b14925e7799ec900d4f94f307` |
| Source base | C44 `ce07b664` + C45 `d02a8942` + C46 `2c896fab` |
| Reference build | C44 `6.1.115-mt6878-gq5012bf1-c29+` |

The source commit is a sanitized C48 publication snapshot, not the local C47
import commit `7a75e19e`. The C45 panel ABI fix is retained in
`panel-ky-vtdr6115-dphy-cmd.c`; the C46 MMC fix lives in the MediaTek mirror.

## Included

- Trusted and pending GQ5012BF1 device-tree overlays.
- `panel-ky-vtdr6115-dphy-cmd.c`, the validated C45 panel implementation.
- `mtk_panel_ext_stock_abi.h`, retained as evidence of the rejected stock
  callback layout.
- YFT touch gesture, Microarray/YFT fingerprint, LN2403 LED, regulator-vibrator,
  ST21NFC, YFT USB and YFT sensor-devinfo board drivers.
- `cust_mt6878_msdc.dtsi`, the platform MMC node referenced by the C46 fix.

## Withheld in C48 (license/redistribution review)

| Path | Embedded material |
| --- | --- |
| `drivers/input/touchscreen/focaltech_touch/` | 118,972-byte stock FT3680 firmware extracted from a vendor `.ko`; `focaltech_flash.h` also lacks a GPL grant |
| `drivers/input/touchscreen/hynitron/` | `firmware_cst816t.inc` and `firmware_cst8xx.inc` |
| `drivers/misc/mediatek/tiny_lcd/` | 1.4 MB vendor logo and LCD init arrays |
| `drivers/power/supply/sh366003/` | Stock SinoWealth AFI/calibration image |

These drivers remain in the canonical kernel tree for private builds. They are
not published until the owner obtains or documents redistribution rights. The
mirror is therefore **partial** and must not be described as complete board
support.

## Build relationship

The combined kernel repository is the canonical build tree. This mirror keeps
the original relative paths and license notices for provenance and review; it
is not compiled independently because Kbuild, generated headers,
`Module.symvers` and KCFI/modversion inputs are coherent only in the combined
tree.

## Licensing

GPL-2.0 is the dominant license. `SOURCE-MANIFEST.json` records the SPDX
identifier found in each file. Files without an SPDX header remain subject to
their original notices; no relicensing is claimed.
