---
title: "Put"
weight: 3
draft: true
---

# LevelDB - Put

Single `Put` of a new key-value pair into LSM tree.


## Config & Command

Config:

- Memtable size limit: 8KB
- SSTable file size limit: 8KB

Command:

```bash
./ycsbcli -d /tmp/helios_leveldb/dbdir -v 64 -f ycsb-traces/a-load.txt --mlim 8192 --flim 8192
./ycsbcli -d /tmp/helios_leveldb/dbdir -f op-traces/put.txt [-s]
```


## Put w/o sync

{{< fig-with-link src="/kvstore/leveldb/vis-put-nosync.svg" ref="/kvstore/leveldb/vis-put-nosync.html" >}}

Resource flow graphs:

### `DBImpl::Write~1`

NULL


## Put w/ sync

{{< fig-with-link src="/kvstore/leveldb/vis-put-sync.svg" ref="/kvstore/leveldb/vis-put-sync.html" >}}

Resource flow graphs:

### `DBImpl::Write~1`

{{< fig-with-link src="/kvstore/leveldb/rtrace-put-sync.svg" ref="/kvstore/leveldb/rtrace-put-sync.svg" >}}
