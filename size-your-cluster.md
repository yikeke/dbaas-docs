---
title: Size Your TiDB Cluster
summary: Learn how to select the number of nodes for your TiDB cluster.
---

# Size Your TiDB Cluster

This document describes how to select the number of nodes for your TiDB cluster.

To ensure high availability of each TiDB Cloud cluster, it is recommended to deploy a specific number of TiDB and TiKV nodes:

- TiDB nodes: Each TiDB Cloud cluster requires at least two TiDB nodes.
- TiKV nodes: Each cluster requires at least 3 TiKV nodes, which are distributed in 3 availability zones.

Data in each TiDB Cloud cluster has 3 replicas, and each replica is distributed in a different availability zone.

> **Note:**
>
> When you scale your TiDB cluster, nodes in the 3 availability zones are increased or decreased at the same time. For how to scale in or scale out a TiDB cluster based on your needs, see [Scale Your TiDB Cluster](scale-tidb-cluter.md).

When you create a cluster, it is recommended to select the number of TiDB and TiKV nodes according to the estimated data volume.

For example:

Supposing the size of your MySQL dump files is 5 TB and the TiDB compression ratio is 70%, the storage needed is 3584 GB.

If you choose the **t1.standard** tier on AWS and each TiKV node has 1900 GB SSD storage, then the required number of TiDB and TiKV nodes are as follows:

- Minimum number of TiKV nodes:  3584 ÷ 1900 × 3 (replica) ≈ 6
- Minimum number of TiDB nodes:  6 ÷ 3 = 2
