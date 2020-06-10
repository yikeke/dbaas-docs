---
title: Back up and Restore TiDB Cluster Data
summary: Learn how to back up and restore your TiDB Cloud cluster.
---

# Back up and Restore TiDB Cluster Data

This document describes how to back up and restore your TiDB cluster data on TiDB Cloud.

## Backup

TiDB Cloud provides two types of data backup: automatic backup and ad-hoc backup.

## Automatic backup

Automatic backups  back up the cluster data every day at the backup time you have set. To set the backup time, perform the following steps:

1. Navigate to the **Backup** tab of a cluster.

2. Click **Auto Setting**. The setting window displays.

3. In the setting window, select **Backup Time** and maximum backup files in **Limit (backup files)**.

4. Click **Confirm**.

> **Note:**
>
> Automatic Backup Retention time = limit backup number × 1 day

## Ad-hoc backup

Ad-hoc backups are user-initiated backups that enable you to back up your data to a known state as needed, and then restore to that state at any time.

To apply an ad-hoc backup to your TiDB cluster, perform the following steps:

1. Navigate to the **Backup** tab of a cluster.

2. Click **Manual** on the upper right.

3. Enter a **Name**.

4. Click **Confirm**. Then your cluster data is backed up.

## Restore

To restore your TiDB cluster data from a backup to a new cluster, perform the following steps:

1. Navigate to the **Backup** tab of a cluster.

2. Select an existing backup in the list, and click **Restore**.

3. In the **Restore** window, enter the cluster **Name** and **Password**.

4. Click **Confirm**.
