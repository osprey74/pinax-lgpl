# pinax-lgpl

[English](README.md)

iOS / iPadOS 向けマルチメディアリーダー **Pinax** の、LGPL 2.1 遵守資料です。

Pinax は [VLCKit](https://code.videolan.org/videolan/VLCKit)（MobileVLCKit）を同梱しています。VLCKit には
GNU Lesser General Public License 2.1 以降が適用されます。このリポジトリでは、LGPL 2.1 第6条 a 項で求められる
資料を提供し、あわせて第6条 c 項の書面による申し出とします。

## 提供するもの

Pinax の各版について、**アプリのバージョンと同じタグ**（`v<版>`）の GitHub Release に次のものを置きます。

- その版で使用した VLCKit のソース一式（上流へのリンクだけではありません）、Pinax が当てた変更（パッチ）、ビルドスクリプト
- その版の Pinax 本体のソースコード。改変した VLCKit で Pinax をビルドできるようにするためのものです。
  **ソース閲覧型の使用許諾**（`SOURCE-LICENSE.md`：自分自身の使用のためのビルドと改変は可、再配布は不可）によります。
  Pinax はオープンソースソフトウェアではありません。
- LGPL 2.1 の全文（[COPYING.LGPL-2.1](COPYING.LGPL-2.1)）

`vlckit-*` のタグの Release には、Pinax がビルドした MobileVLCKit のバイナリと、対応するソースを置きます。

## VLCKit への変更

Pinax は公式のバイナリを使わず、VLCKit 3.7.5 をソースからビルドし、GPL で許諾されたコードを外しています。

- **zvbi**（テレテキストの解読）：`src/packet-830.c` と `src/pdc.c` が GPL version 2 だけで許諾されているため。
  テレテキストは VLC の LGPL の `telx` モジュールで扱います。
- GPL-2+ のソースを持つ VLC のモジュール：`rotate`、`vod_rtsp`、`stream_out_rtp`、`syslog`、`mono`、
  `dolby_surround_decoder`、`dummy`（control）
- デインターレースの **yadif**・yadif2x の方式と、FFmpeg の AArch64 向け **AC-3 DSP** のコード。この 2 つは、
  Small Bricktory が [bop-vlckit](https://github.com/smallbricktory/bop-vlckit)（LGPL-2.1）で公開しているパッチを
  使っています。上の GPL のモジュールも、同所の分析で指摘されたものです。
- FFmpeg の AArch64 向け **CRC32** のアセンブリ（`libavutil/aarch64/crc.S`、GPL-2+）。CRC32 は C 言語版の処理を使います。

ビルドのたびに、GPL のライブラリの記号と、コンパイルされた全ソースファイルの許諾文を検査しています。

### 訂正

最初のビルド `vlckit-3.7.5-pinax.1` は zvbi だけを外したもので、**上に挙げた GPL-2+ のコードがまだ含まれています**。
以前のこの README は、含まれていないと誤って記していました。このビルドを Pinax で配布したことはありません。
`vlckit-3.7.5-pinax.2` 以降を使ってください。

## 保存期間

各版の資料は、その版の配布を終えてから少なくとも 3 年間保存します。

## 利用者の権利

利用者は、自分で使うために VLCKit を改変して Pinax をビルドすること、およびその改変のデバッグのために
Pinax をリバースエンジニアリングすることができます。

## 連絡先

資料の請求やお問い合わせは [Issues](https://github.com/osprey74/pinax-lgpl/issues) からお願いします。
