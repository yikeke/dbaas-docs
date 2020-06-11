---
title: Export Data from TiDB Cloud
summary: Learn how to export data from your TiDB Cloud cluster.
---

# Export Data from TiDB Cloud

This document describes how to export data from your TiDB Cloud cluster.

TiDB Cloud automatically does a backup for your TiDB clusters, you can restore the backup data to a new TiDB cluster. This can safely protect you from losing data in catastrophe disasters.

But sometimes you might still want to export data outside TiDB Cloud. Because TiDB is a MySQL compatible database, you can easily export data outside TiDB Cloud just as what you do when exporting data from MySQL.

You can also use the same tool [Dumpling](https://github.com/pingcap/dumpling) for exporting data outside TiDB Cloud:

1. Install Dumpling.

    ```
    wget https://download.pingcap.org/dumpling-nightly-linux-amd64.tar.gz
    tar xzf dumpling-nightly-linux-amd64.tar.gz
    chmod +x dumpling
    sudo mv dumpling /usr/local/bin/dumpling
    ```

2. Export your TiDB Cloud data using Dumpling.

    ```
    dumpling -h ${tidb-endpoint} -P 3306 -u ${user} -F 67108864 -t 4 -o /path/to/export/dir
    ```

    If you want to backup specific databases, use `-B` to specify comma separated database names.

    The minimum permission requirement are as follows:

    - `SELECT`
    - `RELOAD`
    - `LOCK TABLES`
    - `REPLICATION CLIENT`

    Currently, Dumpling only supports the Mydumper format output, which can be easily restored into MySQL compatible databases by using [TiDB Lightning](https://github.com/pingcap/tidb-lightning).
