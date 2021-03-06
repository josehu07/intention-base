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

{{< fig-with-link src="/kvstore/leveldb/vis-get-mmap.svg" ref="/kvstore/leveldb/vis-get-mmap.html" >}}

Resource flow graphs:

### `Version::ForEachOverlapping~1`

NULL


## Get w/ read

{{< fig-with-link src="/kvstore/leveldb/vis-get-read.svg" ref="/kvstore/leveldb/vis-get-read.html" >}}

Resource flow graphs:

### `Version::ForEachOverlapping~1` (search chain)

{{< fig-with-link src="/kvstore/leveldb/rtrace-get-read.svg" ref="/kvstore/leveldb/rtrace-get-read.svg" >}}

### `TableCache::Get~12` (single check in one sstable)

(target data block happens to be the last block before index)

{{< fig-with-link src="/kvstore/leveldb/rtrace-get-read-1table.svg" ref="/kvstore/leveldb/rtrace-get-read-1table.svg" >}}
