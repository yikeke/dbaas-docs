---
title: Service Level Agreement (SLA)
summary: Learn about the Service Level Agreement (SLA) in TiDB Cloud.
---

# Service Level Agreement (SLA)

This service level agreement applies only to TiDB Cloud production clusters.

## Definitions

The following definitions apply to the SLA:

- "Month" refers to the calendar month.

- "Monthly Uptime Percentage" is calculated per TiDB Cloud cluster on a monthly basis and is calculated as:

    (total minutes in month - unavailable minutes in month) ÷ total minutes in month × 100

- "Unavailable minutes in month" is the total number of minutes that a single TiDB Cloud cluster is unavailable in a monthly billing cycle. If all attempts to establish connections to the cluster fail within one minute, the minute is considered unavailable. A TiDB Cloud cluster deployed in part of the month is assumed to be 100% available during the undeployed part of the month.

- "Monthly Service Fee" means the total fee you paid for a particular TiDB Cloud cluster in the month.

- "Service Credit" is the percentage of the monthly service fee to be credited to you if TiDB cloud approves your claim.

## Service Commitment

TiDB Cloud will use commercially reasonable efforts to make TiDB Cloud clusters available with a monthly uptime percentage of at least 99.99% during any monthly billing cycle.

## Service Credit

If we do not achieve and maintain the monthly uptime percentages, then you may be eligible for a service credit as described below.

| Monthly Uptime Percentage | Service Credit |
| :--| :-- |
| Less than 99.99% but equal to or greater than 99.0% | 10% |
| Less than 99.0% but equal to or greater than 95.0% | 25% |
| Less than 95.0% | 100% |

## Credit Request

To receive a service credit, you must submit a claim by creating a work order through the TiDB Cloud support center, To be eligible, the credit request must be received by us by the end of the second billing cycle after which the incident occurred. The necessary information for the work order must include:

- A detailed description of the event that caused the service unavailable
- Downtime and duration
- Descriptions of your attempts to resolve the downtime at the time of occurrence

If we confirm that the monthly uptime percentage is less than the service commitment, we will issue the service credit to you within one billing cycle following the month in which the request occurred. If the submission is overdue, or you fail to provide the necessary information, you will lose your eligibility for the service credit. service credits must not be transferred or used in any other account.

## Limitations

"Minutes unavailable in month" does not include, and you will not be eligible for a service credit for, any performance or availability issue that results from:

- Force majeure, such as natural disasters, wars, terrorist ACTS, riots, government actions, etc.
- Network or equipment failure between the customer's site and the TiDB Cloud;
- TiDB Cloud advance notice for maintenance, including but not limited to: system upgrade, maintenance, etc.
- Caused by the cloud service provider, including but not limited to: network, hardware, software failure and system maintenance;
- An attack on the client's application;
- The client's program read/write exceeds the system load;
- Loss or leakage of data, passwords or passwords caused by improper confidentiality of the customer;
- Does not follow TiDB Cloud product usage documentation or usage recommendations;
- Does not follow appropriate safety practices;

This service level agreement is effective as of August 1, 2020, and TiDB Cloud is entitled to modify the terms of this SLA. TiDB Cloud will notify you of any changes to the terms of this SLA 60 days in advance by website announcement or email. If you disagree with TiDB Cloud's changes to the SLA, you have the right to stop using the TiDB Cloud service, and if you continue to use the TiDB Cloud service, you are deemed to have accepted the modified SLA.
