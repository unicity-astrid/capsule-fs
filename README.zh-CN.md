# astrid-capsule-fs

[![License: MIT OR Apache-2.0](https://img.shields.io/badge/License-MIT%20OR%20Apache--2.0-blue.svg)](LICENSE-MIT)
[![MSRV: 1.94](https://img.shields.io/badge/MSRV-1.94-blue)](https://www.rust-lang.org)

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md)

**面向 [Astrid OS](https://github.com/unicity-astrid/astrid) 智能体的文件系统工具。**

在操作系统模型中，此 capsule 相当于 coreutils 软件包。它让智能体能够通过内核的 VFS airlock 读取、写入、搜索和浏览工作区文件系统。

## 工具

| 工具 | 描述 |
|---|---|
| `read_file` | 读取文件内容，可选择行范围（`start_line`、`end_line`） |
| `write_file` | 将内容写入文件 |
| `replace_in_file` | 替换精确匹配的字符串（匹配 0 次或超过 1 次时拒绝操作） |
| `list_directory` | 列出目录中的条目 |
| `grep_search` | 递归搜索内容，并限制深度、文件数和匹配数 |
| `create_directory` | 创建目录 |
| `delete_file` | 删除文件（仅限会话中创建的文件，暂不支持 whiteout） |
| `move_file` | 移动文件，大小上限为 10MB，并提供存在性检查和失败回滚 |

所有操作都通过 VFS airlock 进行。在访问主机文件系统之前，内核会强制实施路径边界、写时复制隔离和能力检查。

## 开发

```bash
cargo build --target wasm32-unknown-unknown --release
```

## 许可证

采用 [MIT](LICENSE-MIT) 和 [Apache 2.0](LICENSE-APACHE) 双重许可。

版权所有 (c) 2025-2026 Joshua J. Bouw 和 Unicity Labs。
