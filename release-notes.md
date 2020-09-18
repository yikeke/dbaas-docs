---
title: TiDB Cloud Release Notes
summary: Learn about the release notes of TiDB Cloud.
---

# TiDB Cloud Release Notes

This page lists the release notes of [TiDB Cloud](https://pingcap.com/products/tidbcloud).

## September 14, 2020

* Fix monitoring metrics by adding the `region` label
* Fix the issue that non-HTAP clusters cannot be scaled

## September 11, 2020

* Customers now can access TiDB using a public endpoint with traffic filters
* Add the time zone indicator at the auto backup settings dialog
* Fix the broken invitation link when registration is not finished

## September 4, 2020

* Fix an incorrect URL in invitation Email

## September 1, 2020

* Add the ability for customers to create and manage a new type of cluster: h1.standard
    * Customers now have the option of t1.tiny, t1.standard and h1.standard
    * H1.standard uses TiFlash to utilize the Analytical Processing of the TiDB cluster
* Adjust the tiny cluster instance type and minimum TiDB node count
* Adjust the tiny and standard cluster price to align with changes to the instance types

## August 6, 2020

* Change email support to visiting TiDB Cloud Customer Support
* Add the simple 2fa feature for custom email login
* Add the feature of setting up VPC peering
* Add custom email support for signup/login

## July 17, 2020

* Adjust the default retention of automated daily backup to 7 days
* Add reasons at tooltip for clusters in unhealthy status
* Fix the issue that when the initial credit is 0, users can still create a cluster
* Optimize the integration of Dashboard
* Send emails when adding credits for customers
* Add the tenant ID in the tenant preference page
* Optimize the reasonable notice message for user's quota limit
* Fix backup/restore metrics
