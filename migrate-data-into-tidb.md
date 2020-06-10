---
title: Migrate Data into TiDB
summary: Learn how to export data from MySQL compatible databases, and then import data into your TiDB Cloud cluster.
---

# Migrate Data into TiDB

TiDB Cloud is a MySQL compatible relational database. So data in MySQL compatible databases such as self-managed MySQL database, AWS Aurora, and Google Cloud SQL can be easily migrated to TiDB Cloud. This document describes how to export data from MySQL compatible databases, and then import data into TiDB Cloud.

> **Note:**
>
> TiDB Cloud currently only supports the following CI collations:
> - utf8_general_ci
> - utf8mb4_general_ci
>
> Before migrating data from MySQL into TiDB Cloud, make sure the supported collations satisfy your requirements, otherwise the data cannot be imported into TiDB Cloud.

To migrate data from MySQL compatible databases, first [export data from MySQL compatible databases](#export-data-from-mysql-compatible-databases), and then [import data into TiDB Cloud](#import-data-into-tidb-cloud).

## Export data from MySQL compatible databases

[Dumpling](https://github.com/pingcap/dumpling) is a MySQL compatible database backup tool. You need to use Dumpling to export data from MySQL.

1. Install Dumpling:

    ```
    wget https://download.pingcap.org/dumpling-nightly-linux-amd64.tar.gz
    tar xzf dumpling-nightly-linux-amd64.tar.gz
    chmod +x dumpling
    sudo mv dumpling /usr/local/bin/dumpling
    ```

2. Export your MySQL database using Dumpling:

    ```
    dumpling -h <mysql-host> -P 3306 -u <user> -F 64MiB -t 8 -o /path/to/export/dir
    ```

    If you want to back up specific databases, use `-B` to specify comma separated database names.

    The minimum permission requirements are as follows:

    - `SELECT`
    - `RELOAD`
    - `LOCK TABLES`
    - `REPLICATION CLIENT`

## Import data into your TiDB Cloud cluster

After you have exported your MySQL database using Dumpling, you can use [TiDB Lightning](https://github.com/pingcap/tidb-lightning) to import the data into TiDB Cloud.

1. Install TiDB Lightning:

    ```
    wget https://download.pingcap.org/tidb-toolkit-v4.0.0-linux-amd64.tar.gz
    tar xzf tidb-toolkit-v4.0.0-linux-amd64.tar.gz
    sudo mv tidb-toolkit-v4.0.0-linux-amd64/bin/tidb-lightning* /usr/local/bin/
    ```

2. Import data using TiDB Lightning:

    ```
    tidb-lightning -backend=tidb -check-requirements=false -d=/path/to/export/dir -server-mode=false -tidb-host=${tidb_endpoint} -tidb-port=4000 -tidb-user=${user} -tidb-password=${password}
    ```
