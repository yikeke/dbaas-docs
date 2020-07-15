---
title: Set up VPC Peering Connections
summary: Learn how to set up VPC peering connections.
---

# Set up VPC Peering Connections

To connect your application to TiDB Cloud, you need to set up [VPC peering](glossary.md#vpc-peering) with TiDB Cloud. It's one step of [Connect to Your TiDB Cluster](connect-to-tidb-cluster.md). This document walks you through setting up VPC peering connections on AWS or GCP.

Currently, TiDB Cloud only supports VPC peering in the same region. TiDB clusters in the same region are created in a VPC with the `10.250.0.0/16` CIDR (Classless Inter-Domain Routing) block. VPC peering setup differs among cloud providers.

## On AWS

1. Make sure all your application servers that will visit the TiDB cluster are in the same VPC. The VPC CIDR must not overlap with TiDB Cloud VPC CIDR `10.250.0.0/16`.

    If your VPC has already peered with other VPCs, make sure all the peered VPCs are not overlapped with `10.250.0.0/16`.

2. Visit the [TiDB Cloud support page](https://support.pingcap.com) and submit a request to provide the following information:

    - VPC ID: `<app-vpc-id>`
    - Region: `<app-region>`
    - Account ID: `<app-account-id>`

3. We will create a VPC peering for your VPC and reply with the following information in the request:

    - TiDB peer connect id: `<pcx-tidb-to-app-id>`
    - TiDB private hosted zone for you: `<tidb-phz-id>`

4. Confirm to accept the peer connection request in your AWS account.

    ```
    aws ec2 accept-vpc-peering-connection --vpc-peering-connection-id <pcx-tidb-to-app-id>
    ```

5. Find `<app-route-table-id>` via AWS command line.

    ```
    aws ec2 describe-route-tables --region <app-region> --filters Name=vpc-id,Values=<app-vpc-id> --query 'RouteTables[*].RouteTableId'
    ```

6. Add a route to the TiDB Cloud VPC for each of your VPC subnet route tables.

    ```
    aws ec2 create-route --route-table-id <app-route-table-id> --destination-cidr-block 10.250.0.0/16 --vpc-peering-connection-id <pcx-tidb-to-app-id>
    ```

7. Make sure you have enabled private DNS hosted zone support for your VPC.

    ```
    aws ec2 modify-vpc-attribute --vpc-id <app-vpc-id> --enable-dns-hostnames
    aws ec2 modify-vpc-attribute --vpc-id <app-vpc-id> --enable-dns-support
    ```

8. Associate your VPC with the private hosted zone of TiDB `<tidb-phz-id>`.

    ```
    aws route53 associate-vpc-with-hosted-zone --hosted-zone-id <tidb-phz-id> --vpc VPCRegion=<app-region>,VPCId=<app-vpc-id>
    ```

## On GCP

1. Contact the TiDB Cloud support team to provide information about your application GCP project:

    - Application GCP project ID: `<app-project-id>`
    - VPC network name: `<vpc-network-name>`

2. The TiDB Cloud support team will create a VPC peering for your VPC and provide the following information:

    - TiDB Cloud project ID: `<tidb-project-id>`
    - TiDB Cloud network name: `<tidb-network-name>`

3. Execute the following command to finish the VPC peering setup:

    ```
    gcloud beta compute networks peerings create <your -peer-name> --project <app-project-id> --network <vpc-network-name> --peer-project <tidb-project-id> --peer-network <tidb-network-name>
    ```

    > **Note:**
    >
    > You can name `<your-peer-name>` as you like.
