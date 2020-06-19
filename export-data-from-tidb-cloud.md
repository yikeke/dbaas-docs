---
title: Export Data from TiDB
summary: This page has instructions for exporting data from your TiDB cluster in TiDB Cloud.
---

# Export Data from TiDB

This page describes how to export data from your cluster in TiDB Cloud.

Daily backups are automatically scheduled for your TiDB clusters in TiDB Cloud. You can pick a backup snapshot and restore it into a new TiDB cluster at any time. Automated backup can reduce your losses in extreme disaster situations.

TiDB does not lock-in your data, sometimes you still want to be able to migrate data from TiDB to other data platforms. Because TiDB is highly compatible with MySQL, any export tool suitable for MySQL can also be used for TiDB.

You can use the same tool [Dumpling](https://github.com/pingcap/dumpling) for data export:

1. Install Dumpling.

    ```
    wget https://download.pingcap.org/dumpling-nightly-linux-amd64.tar.gz
    tar xzf dumpling-nightly-linux-amd64.tar.gz
    chmod +x dumpling
    sudo mv dumpling /usr/local/bin/dumpling
    ```

2. Export your data using Dumpling from TiDB.

    ```
    dumpling -h ${tidb-endpoint} -P 3306 -u ${user} -F 67108864 -t 4 -o /path/to/export/dir
    ```

    If you want to export only the specified databases, use `-B` to specify a comma separated list of database names.

    The minimum permissions required are as follows:

    - `SELECT`
    - `RELOAD`
    - `LOCK TABLES`
    - `REPLICATION CLIENT`

    Currently, Dumpling only supports the Mydumper format output, which can be easily restored into MySQL compatible databases by using [TiDB Lightning](https://github.com/pingcap/tidb-lightning).
