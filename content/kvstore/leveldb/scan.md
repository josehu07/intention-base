---
title: "Scan"
weight: 5
draft: true
---

# LevelDB - Scan

Range query over a sufficiently large range using the `Iterator` interface, across an LSM tree image of up to level-2.


## Config & Command

Config:

- Memtable size limit: 8KB
- SSTable file size limit: 8KB

Command:

```bash
./ycsbcli -d /tmp/helios_leveldb/dbdir -v 64 -f ycsb-traces/d-load.txt --mlim 8192 --flim 8192
./ycsbcli -d /tmp/helios_leveldb/dbdir -f op-traces/scan.txt
```


## Range Query

{{< fig-with-link src="/kvstore/leveldb/vis-scan.svg" ref="/kvstore/leveldb/vis-scan.html" >}}

Resource flow graphs:

### `do_ycsb~1` (main iterator loop)

{{< fig-with-link src="/kvstore/leveldb/rtrace-scan.svg" ref="/kvstore/leveldb/rtrace-scan.svg" >}}

### `IteratorWrapper::Next~606` (single step into one sstable)

{{< fig-with-link src="/kvstore/leveldb/rtrace-scan-1table.svg" ref="/kvstore/leveldb/rtrace-scan-1table.svg" >}}
