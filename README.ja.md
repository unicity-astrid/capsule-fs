# astrid-capsule-fs

[![License: MIT OR Apache-2.0](https://img.shields.io/badge/License-MIT%20OR%20Apache--2.0-blue.svg)](LICENSE-MIT)
[![MSRV: 1.94](https://img.shields.io/badge/MSRV-1.94-blue)](https://www.rust-lang.org)

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md)

**[Astrid OS](https://github.com/unicity-astrid/astrid) エージェント向けのファイルシステムツール。**

OS モデルにおいて、この capsule は coreutils パッケージに相当します。エージェントはカーネルの VFS airlock を介して、ワークスペースのファイルシステムを読み書き、検索し、その中をたどることができます。

## ツール

| ツール | 説明 |
|---|---|
| `read_file` | 任意の行範囲（`start_line`、`end_line`）を指定してファイルの内容を読み取ります |
| `write_file` | 内容をファイルに書き込みます |
| `replace_in_file` | 完全一致する文字列を置換します（該当箇所が 0 件または 2 件以上の場合は拒否されます） |
| `list_directory` | ディレクトリ内の項目を一覧表示します |
| `grep_search` | 深さ、ファイル数、一致数の上限を設けて内容を再帰的に検索します |
| `create_directory` | ディレクトリを作成します |
| `delete_file` | ファイルを削除します（セッション中に作成されたファイルのみ。whiteout はまだサポートされていません） |
| `move_file` | 10MB のサイズ上限、存在確認、失敗時のロールバックを伴ってファイルを移動します |

すべての操作は VFS airlock を経由します。ホストファイルシステムへのアクセスが発生する前に、カーネルがパス境界、コピーオンライトによる分離、ケイパビリティチェックを適用します。

## 開発

```bash
cargo build --target wasm32-unknown-unknown --release
```

## ライセンス

[MIT](LICENSE-MIT) と [Apache 2.0](LICENSE-APACHE) のデュアルライセンスです。

Copyright (c) 2025-2026 Joshua J. Bouw and Unicity Labs.
