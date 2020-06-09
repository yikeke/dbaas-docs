---
title: TiDB Cloud Quick Start
summary: Sign up quickly to try TiDB Cloud and create your TiDB cluster.
category: quick start
---

# TiDB Cloud Quick Start

This document describes how to sign up for a trial of TiDB Cloud and how to create your TiDB cluster.

## Overview

The most commonly used operations of TiDB Cloud are as follows:

- [Sign up for a trial](#sign-up-for-a-trial): contact us through the website for a trial, and create your account.
- [Create a cluster](#create-a-cluster): how to create your first cluster, select cloud provider, region, cluster tier, node number, and so on.
- [Secure Database Connections](secure-database-connections.md): connect to your TiDB Cloud cluster via a SQL client, or SQL shell.
- [Migrate from MySQL](t-b-d): migrate your MySQL data to the TiDB Cloud cluster.  

## Sign up for a trial

Now you can visit TiDB Cloud to apply for a trial.

1. Visit <https://pingcap.com/en/product/tidb-cloud/apply>, and submit the following information:

    - Work email
    - First name
    - Last name
    - Company name

2. Finish the account setting. PingCAP support staff will contact you to offer help.

3. After the setting, you will receive an account activation email. Click the verification link in the email to access your TiDB Cloud account.

4. You can invite other members to join your organization after your login. Refer to [Invite a team member](t-b-d) for details.

## Create a cluster

1. Log in to TiDB Cloud.

    Open <https://tidbcloud.com> in a browser and click **Sign in with Google**. The TiDB Cluster page displays.

2. Select Cloud Provider.

    On the **TiDB Cluster** page, click the cloud service provider icon on the left of the top navigation bar, and select the cloud provider.

    ![Select Cloud Provider](/media/select-cloud-provider.png)

3. Access the **Create Cluster** page.

    On the TiDB Cluster page, click **Create Cluster** on the upper right. The Create Cluster page is displayed.

4. Set the cluster name and the root password.

    1. In the **Cluster Name** field, enter a name for your TiDB Cloud cluster.
    2. In the **Root Password** field, enter a root password.

5. Select **Region**.

    Click to select the region where your TiDB cluster is deployed. Future scaling will all be under the chosen region. You cannot change it after the cluster is created.

6. Select **Tier**.

    Click to select your cluster tier, which determines the throughput and performance of your cluster. You cannot change it after the cluster is created. See [Cluster Tiers](t-b-d) for tier details.

7. Select the number of nodes.

    Set the number of your TiDB nodes and TiKV nodes respectively by clicking the plus or the minus sign. See [Size Your Cluster](t-b-d) for details.

8. Click **Submit**.

    Your TiDB Cloud cluster will be successfully created in approximately 5-10 minutes.
