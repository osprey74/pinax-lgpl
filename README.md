# pinax-lgpl

[日本語](README-ja.md)

LGPL 2.1 compliance materials for **Pinax**, an iOS / iPadOS multimedia reader.

Pinax includes [VLCKit](https://code.videolan.org/videolan/VLCKit) (MobileVLCKit), which is licensed under the
GNU Lesser General Public License version 2.1 or later. This repository provides the materials required by
section 6 (a) of the LGPL 2.1, and serves as the written offer under section 6 (c).

## What is provided

For each released version of Pinax, a GitHub Release with the **same tag as the app version** (`v<version>`) contains:

- The VLCKit source code used for that version (full source, not only a link to upstream), together with the
  patch applied by Pinax and the build scripts
- The source code of Pinax itself for that version, so that you can build Pinax with a modified VLCKit.
  It is provided under a **source-available license** (`SOURCE-LICENSE.md`: building and modifying for your own
  personal use is permitted; redistribution is not). Pinax is not open source software.
- The full text of the LGPL 2.1 ([COPYING.LGPL-2.1](COPYING.LGPL-2.1))

Releases tagged `vlckit-*` contain the MobileVLCKit binary built by Pinax and the corresponding source.

## Changes made to VLCKit

Pinax builds VLCKit 3.7.5 from source instead of using the official binary, and removes code licensed under the
GPL:

- **zvbi** (teletext decoding): `src/packet-830.c` and `src/pdc.c` are GPL-2 only. Teletext goes through VLC's
  LGPL `telx` module.
- VLC modules with GPL-2+ sources: `rotate`, `vod_rtsp`, `stream_out_rtp`, `syslog`, `mono`,
  `dolby_surround_decoder`, `dummy` (control)
- The **yadif** / yadif2x deinterlace modes, and FFmpeg's AArch64 **AC-3 DSP** code. These two changes use the
  patches published by Small Bricktory in [bop-vlckit](https://github.com/smallbricktory/bop-vlckit) (LGPL-2.1),
  whose analysis also pointed out the GPL modules above.
- FFmpeg's AArch64 **CRC32** assembly (`libavutil/aarch64/crc.S`, GPL-2+). CRC32 uses the C implementation.

Each build is checked for symbols of GPL libraries and for the license headers of every compiled source file.

### Correction

The first build, `vlckit-3.7.5-pinax.1`, removed only zvbi and **still contains the GPL-2+ code listed above**,
although this README previously said otherwise. It was never shipped in Pinax. Use `vlckit-3.7.5-pinax.2` or later.

## Retention

Materials for each version are kept for at least three years after distribution of that version ends.

## Your rights

You may modify VLCKit for your own use, build Pinax with it, and reverse engineer Pinax to debug such
modifications.

## Contact

Please open an [issue](https://github.com/osprey74/pinax-lgpl/issues) to request materials or ask questions.
