---
title: Monitor a TiDB Cluster
summary: Learn how to monitor your TiDB cluster.
---

# Monitor a TiDB Cluster

This document describes how to monitor a TiDB cluster on TiDB Cloud.

## Cluster status and node status

You can see the current status of each running cluster on the cluster page.

### Cluster Status

| Cluster status | Description |
|:--|:--|
| **Normal** | Normal running (including data migration) |
| **Creating** | Creating the cluster |
| **Scaling** | Scaling the TiKV/TiDB nodes |
| **Upgrading** | Upgrading the TiDB version |
| **Unavailable** | The TiDB Cloud service is not available |
| **Unhealthy** | Part of nodes are unavailable, not enough replicas, and so on |
| **Recovering** | Backup recovery |

### TiDB node status

| TiDB node status | Description |
|:--|:--|
| **Normal** | Normal running |
| **Creating** | Creating the node |
| **Unavailable** | The TiDB node is not available |
| **Terminating** | The TiDB node is terminating |

### TiKV node status

| TiKV node status | Description |
|:--|:--|
| **Normal** | Normal running |
| **Creating** | Creating the node |
| **Unavailable** | The TiKV node is not available |
| **Terminating** | The TiKV node is terminating |
| **Leaving** | Migrating the current node data before termination |

## Monitoring metrics

On the **Overview** page of the cluster, you can view the commonly used metrics of the cluster.

1. Navigate to the **TiDB Cluster** list page.

2. Click the name of the selected cluster, and go to the **Overview** page of the cluster.

    Currently, the metrics include Total QPS, Latency, Connections, Storage Size, TiDB CPU, TiKV CPU, TiKV IO Read, and TiKV IO Write.
