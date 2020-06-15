---
title: Select Your Cluster Tier
summary: Learn how to select your cluster tier on TiDB Cloud.
---

# Select Your Cluster Tier

This document describes how to select your cluster tier on TiDB Cloud.

## Cluster Tier overview

When creating a cluster, you need to select a cluster tier, which determines the throughput and performance of your cluster. Different cluster tiers provide different TiDB and TiKV node instance types. Different tiers are provided for AWS and GCP.

> **Note:**
>
> You cannot change the selected tier after your cluster is created.

## AWS Tiers

| Cluster tier | Node | CPU | Memory | Storage | Scenario |
| :-- | :-- | :-- | :-- | :-- | :-- |
| t1.tiny | TiKV | 2 vCPU | 4 G | 50 G EBS | Testing or development |
| t1.tiny | TiDB | 2 vCPU | 2 G | / | Testing or development |
| t1.standard | TiKV | 8 vCPU | 61 G | 1900 G NVMe | Production |
| t1.standard | TiDB | 8 vCPU | 16 G | / | Production |
| t1.highcpu | TiKV | 16 vCPU | 122 G | 3800 G NVMe | Production (mission-critical applications, high throughput, low latency) |
| t1.highcpu | TiDB | 8 vCPU | 16 G | / | Production (mission-critical applications, high throughput, low latency) |

## GCP Tiers

| Cluster tier | Node | CPU | Memory | Storage | Scenario |
| :-- | :-- | :-- | :-- | :-- | :-- |
| t1.tiny | TiKV | 1 vCPU | 3.75 G | 50 G | Testing or development|
| t1.tiny | TiDB | 1 vCPU | 3.75 G | / | Testing or development|
| t1.standard | TiKV | 8 vCPU | 64 G | 1125 G | Production |
| t1.standard | TiDB | 8 vCPU | 32 G | / | Production |
| t1.highcpu | TiKV | 16 vCPU | 128 G | 1125 G | Production (mission-critical applications, high throughput, low latency) |
| t1.highcpu | TiDB | 8 vCPU | 32 G | / | Production (mission-critical applications, high throughput, low latency) |
