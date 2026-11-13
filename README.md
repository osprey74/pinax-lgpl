# pinax-lgpl

[日本語](README-ja.md)

LGPL 2.1 compliance materials for **Pinax**, an iOS / iPadOS multimedia reader.

Pinax includes [VLCKit](https://code.videolan.org/videolan/VLCKit) (MobileVLCKit), which is licensed under the
GNU Lesser General Public License version 2.1 or later. This repository provides the materials required by
section 6 (a) of the LGPL 2.1, and serves as the written offer under section 6 (c).

## What is provided

For each released version of Pinax, a GitHub Release with the **same tag as the app version** contains:

- The VLCKit source code used for that version (full source, not only a link to upstream), together with the
  patch applied by Pinax and the build script
- The Pinax application in relinkable object form (static library / object files) and instructions for relinking
  it with a modified VLCKit
- The full text of the LGPL 2.1 ([COPYING.LGPL-2.1](COPYING.LGPL-2.1))

Releases tagged `vlckit-*` contain the MobileVLCKit binary built by Pinax and the corresponding source,
used during development.

## Changes made to VLCKit

Pinax builds VLCKit 3.7.5 from source instead of using the official binary.
The only change is to disable **zvbi** (teletext decoding), because two of its files (`src/packet-830.c` and
`src/pdc.c`) are licensed under the GPL version 2 only. The build is checked to contain no symbols from
GPL-licensed libraries.

## Retention

Materials for each version are kept for at least three years after distribution of that version ends.

## Your rights

You may modify VLCKit for your own use, relink it with Pinax, and reverse engineer Pinax to debug such
modifications. The Pinax terms of use do not prohibit this.

## Contact

Please open an [issue](https://github.com/osprey74/pinax-lgpl/issues) to request materials or ask questions.
