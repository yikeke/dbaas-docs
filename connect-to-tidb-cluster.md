---
title: Connect to Your TiDB Cluster
summary: Connect to your TiDB cluster via a SQL client or SQL shell.
---

# Connect to Your TiDB Cluster

After your TiDB cluster in created on TiDB Cloud, you can use either of the following two methods to connect to your TiDB cluster:

- [Connect via a SQL client](#connect-via-a-sql-client): to connect to the TiDB cluster from your application
- [Connect via SQL shell](#connect-via-sql-shell): to try TiDB SQL and test out TiDB’s compatibility with MySQL quickly, or administer user privileges

## Connect via a SQL Client

To connect to your TiDB cluster using a SQL client, perform the following steps:

1. Navigate to the **TiDB Cluster** page and find your newly created cluster.

2. Click **Connect**. The **Connect to TiDB** using a SQL client dialog displays.

3. Set up VPC peering. See [Set up VPC Peering](set-up-vpc-peering-connections.md) for details.

4. Use a SQL client to connect to TiDB from your server which has set up VPC peering with TiDB Cloud.

    ```sql
    mysql -u root -h <endpoint> -P 4000 -p
    ```

    > **Note:**
    >
    > Currently, TiDB does not work well with MySQL client 8.0, so you need to use MySQL client 5.7. Or you can add the `--default-auth=mysql_native_password --default-character-set` command line option if you are using MySQL client 8.0.

## Connect via SQL Shell

To connect to your TiDB cluster using SQL shell, perform the following steps:

1. Navigate to the **TiDB Cluster** page and find your newly created cluster.

2. Click **Connect**, select the **Open SQL Shell** tab, and click **Open SQL Shell**.

3. On the prompted **TiDB password** line, enter the root password of the current cluster. Then your application is connected to the TiDB cluster.

## What's next

After you have successfully connected to your TiDB cluster, you can [explore SQL statements with TiDB](https://pingcap.com/docs/stable/basic-sql-operations/).