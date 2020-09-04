---
title: TiDB Cloud Release Notes
summary: Learn about the release notes of TiDB Cloud.
---

# TiDB Cloud Release Notes

This page lists the release notes of [TiDB Cloud](https://pingcap.com/products/tidbcloud).

## September 4, 2020

* Fix the issue of querying tenant failure(record not found)

## September 1, 2020

* Add the ability for customers to create and manage a new type of cluster: h1.standard
  * Customers now have the option of t1.tiny, t1.standard and h1.standard
  * H1.standard uses TiFlash to utilize the Analytical Processing of the TiDB cluster
* Adjust the tiny cluster instance type and minimum TiDB node count
* Adjust the tiny and standard cluster price to align with changes to the instance types

## August 6, 2020

* Change email support to visiting TiDB Cloud Customer Support [#135](https://github.com/pingcap/dbaas-docs/issues/135)
* Add the simple 2fa feature for custom email login [#127](https://github.com/pingcap/dbaas-docs/issues/127)
* Add the feature of setting up VPC peering [#126](https://github.com/pingcap/dbaas-docs/issues/126)
* Add custom email support for signup/login [#99](https://github.com/pingcap/dbaas-docs/issues/99)

## July 17, 2020

* Adjust the default retention of automated daily backup to 7 days [#94](https://github.com/pingcap/dbaas-docs/issues/94)
* Add reasons at tooltip for clusters in unhealthy status [#74](https://github.com/pingcap/dbaas-docs/issues/74)
* Fix the issue that when the initial credit is 0, users can still create a cluster [#95](https://github.com/pingcap/dbaas-docs/issues/95)
* Optimize the integration of Dashboard [#96](https://github.com/pingcap/dbaas-docs/issues/96)
* Send emails when adding credits for customers [#103](https://github.com/pingcap/dbaas-docs/issues/103)
* Add the tenant ID in the tenant preference page [#102](https://github.com/pingcap/dbaas-docs/issues/102)
* Optimize the reasonable notice message for user's quota limit [#93](https://github.com/pingcap/dbaas-docs/issues/93)
* Fix backup/restore metrics [#2140](https://github.com/pingcap/dbaas/pull/2140)
