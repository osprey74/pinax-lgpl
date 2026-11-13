# pinax-lgpl

[English](README.md)

iOS / iPadOS 向けマルチメディアリーダー **Pinax** の、LGPL 2.1 遵守資料です。

Pinax は [VLCKit](https://code.videolan.org/videolan/VLCKit)（MobileVLCKit）を同梱しています。VLCKit には
GNU Lesser General Public License 2.1 以降が適用されます。このリポジトリでは、LGPL 2.1 第6条 a 項で求められる
資料を提供し、あわせて第6条 c 項の書面による申し出とします。

## 提供するもの

Pinax の各版について、**アプリのバージョンと同じタグ**の GitHub Release に次のものを置きます。

- その版で使用した VLCKit のソース一式（上流へのリンクだけではありません）、Pinax が当てた変更（パッチ）、ビルド手順
- 再リンクできる形式の Pinax 本体（静的ライブラリまたはオブジェクトファイル）と、改変した VLCKit と再リンクする手順
- LGPL 2.1 の全文（[COPYING.LGPL-2.1](COPYING.LGPL-2.1)）

`vlckit-*` のタグの Release には、Pinax がビルドした MobileVLCKit のバイナリと、対応するソースを置きます（開発用）。

## VLCKit への変更

Pinax は公式のバイナリを使わず、VLCKit 3.7.5 をソースからビルドしています。
変更点は **zvbi**（テレテキストの解読）を外したことだけです。zvbi のうち 2 つのファイル（`src/packet-830.c`、
`src/pdc.c`）は GPL version 2 だけで許諾されているためです。ビルドしたものに GPL のライブラリの記号が
含まれていないことを検査しています。

## 保存期間

各版の資料は、その版の配布を終えてから少なくとも 3 年間保存します。

## 利用者の権利

利用者は、自分で使うために VLCKit を改変して Pinax と再リンクすること、およびその改変のデバッグのために
Pinax をリバースエンジニアリングすることができます。Pinax の利用規約はこれらを禁じていません。

## 連絡先

資料の請求やお問い合わせは [Issues](https://github.com/osprey74/pinax-lgpl/issues) からお願いします。
