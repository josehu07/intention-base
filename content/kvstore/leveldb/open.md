---
title: "Open"
weight: 2
draft: true
---

# LevelDB - Open

Opening a LevelDB instance, re-building the state from the `.log` file left by the last close, saving it as a new level-0 table.


## Config & Command

Config:

- Memtable size limit: default (4MB)
- SSTable file size limit: default (2MB)

Command:

```bash
./ycsbcli -d /tmp/helios_leveldb/dbdir -v 64 -f ycsb-traces/a-load.txt
```


## Open Dirty DB

{{< fig-with-link src="/kvstore/leveldb/vis-open.svg" ref="/kvstore/leveldb/vis-open.html" >}}

Resource flow graphs:

### `DBImpl::Recover~1` (rebuild from `.log`)

{{< fig-with-link src="/kvstore/leveldb/rtrace-open.svg" ref="/kvstore/leveldb/rtrace-open.svg" >}}
