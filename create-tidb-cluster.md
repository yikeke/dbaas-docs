---
title: Create a TiDB Cloud cluster
summary: Learn how to create your TiDB Cloud cluster.
---

# Create a TiDB Cloud Cluster

This document describes how to create a TiDB Cloud cluster.

<EmbedYouTube videoTitle="TiDB Cloud - Create a Cluster" videoSrcURL="https://www.youtube.com/embed/uGRoKiETSUU?rel=0" />

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

    Click to select your cluster tier, which determines the throughput and performance of your cluster. You cannot change it after the cluster is created. See [Select Your Cluster Tier](select-cluster-tier.md) for details.

7. Select the number of nodes.

    Set the number of your TiDB nodes and TiKV nodes respectively by clicking the plus or the minus sign. See [Size Your Cluster](size-your-cluster.md) for details.

8. Click **Submit**.

    Your TiDB Cloud cluster will be successfully created in approximately 5-10 minutes.
