---
title: "Get"
weight: 4
draft: true
---

# LevelDB - Get

Single `Get` of the latest value (which is at level 2) of a given key from LSM tree.


## Config & Command

Config:

- Memtable size limit: 8KB
- SSTable file size limit: 8KB

Command:

```bash
./ycsbcli -d /tmp/helios_leveldb/dbdir -v 64 -f ycsb-traces/a-load.txt --mlim 8192 --flim 8192
./ycsbcli -d /tmp/helios_leveldb/dbdir -f op-traces/get.txt
```


## Get w/ mmap

[{{< figure src="/kvstore/leveldb/vis-get-mmap.svg" >}}](/kvstore/leveldb/vis-get-mmap.html)

Resource flow graphs:

### `Version::ForEachOverlapping`

NULL


## Get w/ read

[{{< figure src="/kvstore/leveldb/vis-get-read.svg" >}}](/kvstore/leveldb/vis-get-read.html)

Resource flow graphs:

### `Version::ForEachOverlapping`

[{{< figure src="/kvstore/leveldb/rtrace-get-read.svg" >}}](/kvstore/leveldb/rtrace-get-read.svg)
