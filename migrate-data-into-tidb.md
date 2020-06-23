---
title: Migrate Data into TiDB
summary: This page has instructions for migrating data from MySQL compatible databases to TiDB using the Dumpling and TiDB Lightning tools.
---

# Migrate Data into TiDB

TiDB is a relational database highly compatible with MySQL. Therefore, the migration of data from any type of MySQL database to TiDB is very smooth, whether it is from a self-hosted MySQL instance or RDS service provided by the public cloud.

> **Note:**
>
> TiDB currently only supports the following CI collations:
> - utf8_general_ci
> - utf8mb4_general_ci
>
> Before migrating data from MySQL into TiDB, confirm that the supported collations can meet your requirements.

## Step 1. Export data from MySQL compatible databases

You can use several ways to dump data from MySQL, such as using `mysqldump` or `mydumper`. It is recommended to use the [Dumpling](https://docs.pingcap.com/tidb/v4.0/export-or-backup-using-dumpling) tool for higher performance and compatibility with TiDB, which is also one of the open source tools created by PingCAP.

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

    If you want to export only the specified databases, use `-B` to specify a comma separated list of database names.

    The minimum permissions required are as follows:

    - `SELECT`
    - `RELOAD`
    - `LOCK TABLES`
    - `REPLICATION CLIENT`

## Step 2. Import data to your TiDB cluster

You can use [TiDB Lightning](https://docs.pingcap.com/tidb/v4.0/tidb-lightning-overview) to quickly import the files exported from MySQL by `Dumpling` to TiDB.

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
