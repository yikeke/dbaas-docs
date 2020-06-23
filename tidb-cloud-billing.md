---
title: TiDB Cloud Billing
summary: Learn about TiDB Cloud billing.
---

# TiDB Cloud Billing

You need to pay for the cluster nodes you use. In addition, the storage resources occupied by the backup data, and data transfers "in" and "out" of TiDB Cluster are charged separately.

## Node cost

TiDB Cloud lets you pay for your database by the hour, which is ideal for development, testing, and other short-lived workloads. TiDB cloud offers multiple cluster tiers that are equipped with fixed TiDB and TiKV instances. The unit prices of TiDB and TiKV nodes vary in different tiers, and the unit price of TiDB differs from that of TiKV nodes in the same tier.

The pricing formula is as follows:

Cluster tier price per hour = TiDB unit price per hour × TiDB node number + TiKV unit price per hour × TiKV node number

For TiDB / TiKV unit price in different cloud service providers, and different regional node price, refer to <https://pingcap.com/products/tidbcloud>.

## Backup storage cost

TiDB Cloud provides automatic backup and ad-hoc backup, both backups consume the storage. We will charge you based on the maximum capacity of total backups per month.

The storage prices for different cloud providers are as follows:

- AWS

    All backups will be saved in Amazon Simple Storage Service (Amazon S3). You only need to pay the S3 fee and we will not charge you an additional fee. For details, see [Amazon S3 pricing](https://aws.amazon.com/s3/pricing/).

- GCP

    All backups will be saved in GCP cloud storage. You only need to pay the Cloud Storage fee and we will not charge you an additional fee. For details, see [GCP Cloud Storage pricing](https://cloud.google.com/storage/pricing).

## Data Transfer cost

Data transfer costs depend on the cloud service provider where you deployed the cluster. 

- AWS

    TiDB Cloud charges for data transfer between the TiDB cluster load balancer and your server, and the fixed cost of the load balancer. We will charge this fee according to the exact AWS bill, without additional fees. For details, see [AWS Network Load Balancer pricing](https://aws.amazon.com/elasticloadbalancing/pricing/?nc1=h_ls).

- GCP

    TiDB Cloud charges for data transfer between the TiDB cluster load balancer and your server, and the fixed cost of the load balancer. We will charge this fee according to the exact GCP bill, without additional fees.

## Invoices

At the beginning of each month, we will send you the invoice for the previous month’s usage, and deduct the fees from your remaining credits.

The invoice cost includes the node cost, backup storage cost, and data transfer cost of all clusters under your current organization.

Invoice amount = Node cost + Backup storage cost + Data transfer cost - remaining credit

- If the amount of the invoice is greater than credits, we will deduct your credits first, and then deduct the remaining amount from your credit card.
- If the amount of the invoice is less than credits, we will only deduct your credits.

> **Note:**
>
> All billing deductions will be completed through the third-party platform Stripe.

You can view the current usage of this month in the billing console, but only for reference. The final invoice amount still needs to be finalized through the monthly invoice determined in the next month.

To view the invoices list, click **Billing** in the top menu bar. The billing console displays, and the **Invoices** tab displays by default.

## Credits

TiDB Cloud credits can be used to pay monthly bills. If your credits are not used up, they will be used in the next month automatically, until the credits are used up.

> **Note:**
>
> - In the billing deduction, one dollar credit is equivalent to one dollar.
> - Credits can only be used for clusters within the organization. It cannot be transferred to other organizations and cannot be exchanged.

To apply for TiDB Cloud credits, contact the sales for you.

To view your credit details, perform the following steps:

1. Click **Billing** in the top menu bar. The billing console displays.
2. Click the **Credits** tab.

## Payment method setting

Before creating a cluster, or in the billing console, you can bind a valid credit card. We will deduct the fee from the bound credit card according to your cluster usage.

When binding your credit card, you must provide the cardholder's name, email, phone, country/region, card number, valid year and month, and CVC (Card Verification Code).

To add a credit card, perform the following steps:

1. Click **Billing** in the top menu bar. The billing console displays.

2. Click the **Payment Method** tab.

3. Click **Add Credit Card**. The **Add a Card** dialog window displays.

4. Enter the cardholder's name, email, phone, country/region, card number, valid year and month, and CVC (Card Verification Code).

5. Click **Submit**.

> **Note:**
>
> To ensure the security of credit card sensitive data, TiDB Cloud does not save any customer credit card information and save them in the third-party payment platform Stripe. All billing deductions are completed through Stripe.

You can bind multiple credit cards, and set one of them as the default credit card in the payment method of the billing console. After setting, subsequent billings will be automatically deducted from the default credit card.

To set the default credit card:

1. Click **Billing** in the top menu bar. The billing console displays.
2. Click the **Payment Method** tab.
3. Select a credit card in the credit card list, and click **Set as default**.
