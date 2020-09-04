---
title: Set Up VPC Peering Connections
summary: Learn how to set up VPC peering connections.
---

# Set Up VPC Peering Connections

To connect your application to TiDB Cloud, you need to set up [VPC peering](glossary.md#vpc-peering) with TiDB Cloud. It's one step of [Connect to Your TiDB Cluster](connect-to-tidb-cluster.md). This document walks you through setting up VPC peering connections [on AWS](#on-aws) and [on GCP](#on-gcp).

VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IP addresses. Instances in either VPC can communicate with each other as if they are within the same network.

Currently, TiDB Cloud only supports VPC peering in the same region. TiDB clusters in the same region are created in a VPC with the `10.250.0.0/16` CIDR (Classless Inter-Domain Routing) block. So once a VPC peering is set up in the region, all the TiDB clusters created in this region can be connected in your VPC. VPC peering setup differs among cloud providers.

## On AWS

### Step 1: Add VPC peering requests

1. Go to the **Network Access** page and click **Add**.

    ![TiDB Cloud Network Access](media/vpc-peering/tidb-cloud-network-access-dashboard.png)

2. On the **Add VPC Peering** dialog, fill in the required information of your existing AWS VPC:

    - AWS Account ID
    - VPC ID
    - CIDR
    - Region

    You could get these information from your VPC details on the VPC dashboard.

    ![VPC peering](media/vpc-peering/vpc-peering-creating-infos.png)

3. Click **Initialize**. The **Approve VPC Peerings** dialog displays.

    ![Add VPC peering](media/vpc-peering/tidb-cloud-vpc-peering-env-check-information.png)

### Step 2: Approve and configure the VPC peering

Use either of the following two options to approve and configure the VPC peering connection:

- [Option 1: Use AWS CLI](#option-1-use-aws-cli)
- [Option 2: Use the AWS dashboard](#option-2-use-the-aws-dashboard)

#### Option 1: Use AWS CLI

1. Install AWS Command Line Interface (AWS CLI).

    {{< copyable "shell-regular" >}}

    ```bash
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install
    ```

2. Configure AWS CLI according to your account information. To get the information required by AWS CLI, see [AWS CLI configuration basics](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html).

    {{< copyable "shell-regular" >}}

    ```bash
    aws configure
    ```

3. Replace the following variable values with your account information.

    {{< copyable "shell-regular" >}}

    ```bash
    # Set up the related variables.
    pcx_tidb_to_app_id="<TiDB peering id>"
    app_region="<APP Region>"
    app_vpc_id="<Your VPC ID>"
    tidb_phz_id="<TiDB private hosted zone for you>"
    ```

    For example:

    ```
    # Set up the related variables
    pcx_tidb_to_app_id="pcx-069f41efddcff66c8"
    app_region="us-west-2"
    app_vpc_id="vpc-0039fb90bb5cf8698"
    tidb_phz_id="Z07551272U929P4PN8MQT"
    ```

4. Execute the following commands.

    {{< copyable "shell-regular" >}}

    ```bash
    # Accepts the VPC peering connection request.
    aws ec2 accept-vpc-peering-connection --vpc-peering-connection-id "$pcx_tidb_to_app_id"
    ```

    {{< copyable "shell-regular" >}}

    ```bash
    # Creates route table rules.
    aws ec2 describe-route-tables --region "$app_region" --filters Name=vpc-id,Values="$app_vpc_id" --query 'RouteTables[*].RouteTableId' --output text|xargs -d "\t" -n 1|  while read row
    do
        app_route_table_id="$row"
        aws ec2 create-route --route-table-id "$app_route_table_id" --destination-cidr-block 10.250.0.0/16 --vpc-peering-connection-id "$pcx_tidb_to_app_id"
    done
    ```

    {{< copyable "shell-regular" >}}

    ```bash
    # Modifies the VPC attribute to enable DNS-hostname and DNS-support.
    aws ec2 modify-vpc-attribute --vpc-id "$app_vpc_id" --enable-dns-hostnames
    aws ec2 modify-vpc-attribute --vpc-id "$app_vpc_id" --enable-dns-support
    ```

After finishing the configuration, the VPC peering has been created. You can [connect to the TiDB cluster](#step-3-connect-to-the-tidb-cluster-on-the-tidb-cloud) to verify the result.

#### Option 2: Use the AWS dashboard

You can also use the AWS dashboard to configure the VPC peering connection.

1. Confirm to accept the peer connection request in your AWS console.

    1. Sign in to the AWS console and click **Services** on the top menu bar. Enter "VPC" in the search box and come to the VPC service page.

        ![AWS dashboard](media/vpc-peering/aws-vpc-guide-1.jpg)

    2. From the left navigation bar, open the **Peering Connections** page. On the **Create Peering Connection** tab, a peering connection is in the **Pending Acceptance** status.

    3. Confirm the requester owner is TiDB Cloud (`380838443567`). Right click on the peering connection and click **Accept Request** to accept the request.

        ![AWS VPC peering requests](media/vpc-peering/aws-vpc-guide-3.png)

2. Add a route to the TiDB Cloud VPC for each of your VPC subnet route tables.

    1. From the left navigation bar, open the **Route Tables** page.

    2. Search all the route tables that belong to your application VPC.

        ![Search all route tables related to VPC](media/vpc-peering/aws-vpc-guide-4.png)

    3. Edit each route table to add a route with destination to the TiDB Cloud VPC CIDR (`10.250.0.0/16`), and select your peering ID on the **Target** column.

        ![Edit all route tables](media/vpc-peering/aws-vpc-guide-5.png)

3. Make sure you have enabled private DNS hosted zone support for your VPC.

    1. From the left navigation bar, open the **Your VPCs** page.

    2. Select your application VPC.

    3. Right click on the selected VPC. The setting drop-down list displays.

    4. From the setting drop-down list, click **Edit DNS hostnames**. Enable DNS hostnames and click **Save**.

    5. From the setting drop-down list, click **Edit DNS resolution**. Enable DNS resolution and click **Save**.

### Step 3: Connect to the TiDB cluster on TiDB Cloud

1. Navigate to the **TiDB Cluster** page and find your cluster.

2. Click **Connect**. The **Connect to TiDB** dialog displays. You could see the **Status** of the VPC peering is **active**.

3. Access the TiDB Cluster from the instance within the VPC. See [Connect to Your TiDB Cluster](connect-to-tidb-cluster.md).

## On GCP

1. Visit the [TiDB Cloud support page](https://support.pingcap.com) and submit a request to provide the following information about your application GCP project:

    - Application GCP project ID: `<app-project-id>`
    - VPC network name: `<vpc-network-name>`

2. The TiDB Cloud support team will create a VPC peering for your VPC and provide the following information:

    - TiDB Cloud project ID: `<tidb-project-id>`
    - TiDB Cloud network name: `<tidb-network-name>`

3. Execute the following command to finish the VPC peering setup:

    ```{.bash copyable}
    gcloud beta compute networks peerings create <your -peer-name> --project <app-project-id> --network <vpc-network-name> --peer-project <tidb-project-id> --peer-network <tidb-network-name>
    ```

    > **Note:**
    >
    > You can name `<your-peer-name>` as you like.
