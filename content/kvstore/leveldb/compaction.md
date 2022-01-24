---
title: "Compaction"
weight: 6
draft: true
---

# LevelDB - Compaction

Compacting higher-level sstables and pushing the records to lower levels.


## Config & Command

Config:

- Memtable size limit: 8KB
- SSTable file size limit: 8KB

Command:

```bash
./ycsbcli -d /tmp/helios_leveldb/dbdir -v 64 -f ycsb-traces/a-load.txt --mlim 8192 --flim 8192
```


## Compaction Thread Invocation

{{< fig-with-link src="/kvstore/leveldb/vis-compaction.svg" ref="/kvstore/leveldb/vis-compaction.html" >}}

Resource flow graphs:

### `DBImpl::DoCompactionWork~1` (one compaction loop)

{{< fig-with-link src="/kvstore/leveldb/rtrace-compaction.svg" ref="/kvstore/leveldb/rtrace-compaction.svg" >}}

### `DBImpl::CompactMemTable~1` (pushing memtable to level-0)

{{< fig-with-link src="/kvstore/leveldb/rtrace-compaction-memtable.svg" ref="/kvstore/leveldb/rtrace-compaction-memtable.svg" >}}
