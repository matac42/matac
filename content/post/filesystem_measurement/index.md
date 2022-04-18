---
title: "Filesystem measurement"
date: 2022-04-18T14:37:02+09:00
draft: false
tags: [filesystem]
categories: [tec]
---

# ファイルシステムを特徴づける項目は何か

ファイルシステムの特徴を述べるときに、どのような項目について述べたらよいかを考える必要がある。また、ファイルシステムを計測する際にも、それは必要である。ひとまず、列挙してみた。

## Wikipedia調べ

https://en.wikipedia.org/wiki/Comparison_of_file_systems

### Limits

- Maximum filename length
- Allowable characters in directory entries
- Maximum pathname length
- Maximum file size
- Maximum volume size
- Max number of files

いわゆる、性能上限である。数値的に計測可能なものであるから、計測というとこの辺りについて行うと思われる。Allowable characters in directory entriesは対応している文字コードがどれほどあるかである。Max number of filesはcreateできるファイル数の上限である。inodeを用いたファイルシステムの場合、inode領域をinitialize時に確保する都合上、ファイル数の上限 ≒ inode数となる。

### Metadata

- Stores file owner
- POSIX file permissions
- Creation timestamps
- Last access/read timestamps
- Last metadata change timestamps
- Last archive timestamps
- Access control lists
- Security/MAC labels
- Extended attributes/Alternate data streams/forks
- Metadata checksum/ECC

ファイルやディレクトリにどのようなメタデータを持たせることができるかということである。inodeを用いたファイルシステムでは以下のようなメタデータを持つ。

- File type
- Permissions
- Owner ID
- Group ID
- Size of file
- Time last accessed
- Time last modified
- Soft/Hard Links
- Access Control List (ACLs)

### File capabilities

- Hard links
- Symbolic links
- Block journaling
- Metadata-only journaling
- Case-sensitive
- Case-preserving
- File Change Log
- XIP

ファイルに関する機能である。例えば、journalingはファイルシステム上のデータを保護する重要な機能である。

### Block capabilities

- internal snapshotting/branching
- encryption
- deduplication
- Data checksum/ECC
- Persistent Cache
- Multiple Devices
- compression

ブロックに関する機能である。

### Resize capabilities

- Offline grow Online grow Offline shrink
- Online shrink
- add and remove physical volumes

リサイズに関する機能である。

### Allocation and layout policies

- Sparse files
- Block suballocation
- Tail packing
- Extents
- Variable file block size
- Allocate-on-flush
- Copy on write
- Trim support

ファイルやブロックをアロケートする際の機能や規則である。

### OS support

そのファイルシステムがどのOS上で動作するか、ということである。